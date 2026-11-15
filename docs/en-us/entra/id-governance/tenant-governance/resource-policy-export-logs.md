<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-export-logs -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# Export Microsoft Entra resource policy logs \(preview\)

Export resource policy evaluation logs to Log Analytics for KQL queries, Azure Storage for archival, or Azure Event Hubs for downstream processing.

For direct request investigation or assignment assessment, use the [Microsoft Graph evaluation audit-log API](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-logs). Export is optional.

The queries summarize exported requests, not tenant-wide resource compliance. Azure destinations can incur separate charges.

## Prerequisites

- A Microsoft Entra ID P1 or P2 tenant license for log export.
- A work or school account with an active [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator) role in the Microsoft Entra tenant to configure diagnostic settings in the [Microsoft Entra admin center](https://entra.microsoft.com).
- An Azure subscription with an existing destination. For the KQL workflow, use a [Log Analytics workspace](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/quick-create-workspace) that you can select as the destination. An Event Hubs-only export doesn't require a workspace.
- For KQL queries in the [Azure portal](https://portal.azure.com), the [Log Analytics Reader](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles/monitor#log-analytics-reader) role on the destination workspace. Microsoft Entra roles don't grant Azure workspace access. For access options, see [Manage access to log data and workspaces](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/manage-access).
- An enabled policy assignment and representative requests that match its resource type and operations.

If you access Log Analytics through the Microsoft Entra admin center instead of the Azure portal, also use the [Reports Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#reports-reader) role. See [Analyze activity logs with Log Analytics](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-analyze-activity-logs-log-analytics).

Activate any eligible roles through Privileged Identity Management \(PIM\) before starting.

## Configure log export

Create the diagnostic setting for the Microsoft Entra tenant, not an application or policy. These steps configure Log Analytics:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) in the tenant whose policies you want to monitor.
2. Browse to **Entra ID** > **Monitoring & health** > **Diagnostic settings**.
3. Select **Add diagnostic setting**.
4. Enter a name, such as `resource-policy-evaluations`.
5. Under **Logs**, select **MicrosoftGraphPolicyLogs**. Selecting **MicrosoftGraphActivityLogs** alone doesn't export policy evaluation details.
6. Under **Destination details**, select **Send to Log Analytics workspace**.
7. Select the destination subscription and workspace, and then select **Save**.
8. Reopen the setting and verify that the category is enabled and the intended workspace is selected.

For other destinations, follow [Configure Microsoft Entra diagnostic settings](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-configure-diagnostic-settings) or [Stream logs to an event hub](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-stream-logs-to-event-hub). For automation, use the tenant-scoped [diagnostic settings resource](https://learn.microsoft.com/en-us/azure/templates/microsoft.aadiam/2017-04-01/diagnosticsettings), not a workspace diagnostic setting.

If the category isn't available, confirm that resource policy log export is enabled for your preview tenant. Don't substitute a different category.

Use the column names shown here for Log Analytics. The Microsoft Graph API uses different property names.

## Verify that evaluations arrive

1. Make an approved request that matches an enabled assignment. Record the UTC time and request ID. A write can change directory data.
2. In the Azure portal, open the destination **Log Analytics workspace**, select **Logs**, and use KQL mode.
3. Run the following query with your Microsoft Entra tenant ID. Once records arrive, [find your recorded request](#investigate-a-specific-request) to confirm it was exported.

```kusto
let targetTenantId = "<tenant-id>";
MicrosoftGraphPolicyLogs
| where TimeGenerated > ago(24h)
| where AadTenantId == targetTenantId
| summarize Evaluations = count(), LastEvaluation = max(TimeGenerated)
```

Use `AadTenantId`, not the workspace's `TenantId`. See the [table reference](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/microsoftgraphpolicylogs) for column definitions.

Allow for [export and ingestion delay](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-configure-diagnostic-settings#basic-process). If no rows appear, check the tenant, destination, time range, and enabled assignment. Requests outside enabled assignments don't produce policy evaluation records; no rows isn't proof of compliance.

## Analyze outcomes over time

1. Replace `<tenant-id>` and adjust the time range for your observation period.
2. Run this query to compare decisions over time and count requests with errors separately:

```kusto
let targetTenantId = "<tenant-id>";
MicrosoftGraphPolicyLogs
| where TimeGenerated > ago(24h)
| where AadTenantId == targetTenantId
| summarize Requests = count(),
    RequestsWithErrors = countif(ErrorPoliciesCount > 0)
    by bin(TimeGenerated, 1h), PolicyDecision
| order by TimeGenerated desc
```

A `deny` decision means blocked. Nonblocking outcomes can use `audit` or `none`; inspect `PolicyDetails` to distinguish violations from errors. Don't count every `none` result as a violation.

## Assess one assignment's impact

1. Enter the tenant and assignment names, and choose a time range covering representative traffic.
2. Run this query to separate violations from loading, applicability, and evaluation errors.
3. Use the caller `AppId` and request details to work with affected application owners on remediation or supported temporary exceptions. Follow [safe deployment](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-safe-deployment) before enabling enforcement.

```kusto
let targetTenantId = "<tenant-id>";
let assignmentName = "<assignment-unique-name>";
MicrosoftGraphPolicyLogs
| where TimeGenerated > ago(7d)
| where AadTenantId == targetTenantId
| mv-expand PolicyDetail = PolicyDetails
| where tostring(PolicyDetail.assignmentUniqueName) == assignmentName
| extend IsApplicable = tobool(PolicyDetail.isApplicable),
    IsCompliant = tobool(PolicyDetail.isCompliant),
    HasError = isnotempty(tostring(PolicyDetail.policyLoadingError))
        or isnotempty(tostring(PolicyDetail.applicabilityEvaluationError))
        or isnotempty(tostring(PolicyDetail.evaluationError))
| summarize MatchedRequests = count(),
    ApplicableRequests = countif(IsApplicable),
    NoncompliantRequests = countif(IsApplicable and IsCompliant == false and HasError == false),
    RequestsWithErrors = countif(HasError)
    by AppId, RequestMethod, TargetResourceName
| order by NoncompliantRequests desc
```

These are selected-assignment results, not the overall enforcement decision. Another assignment can block the same request. `PolicyDetails` can be truncated, so counts reflect retained details, not necessarily all evaluations.

## Investigate a specific request

1. Replace the tenant and request placeholders. If you recorded only the client-supplied identifier, filter on `ClientRequestId` instead of `RequestId`.
2. Run the query and inspect `PolicyDetails` for the assignment, version, reasons, and errors.

```kusto
let targetTenantId = "<tenant-id>";
let targetRequestId = "<request-id>";
MicrosoftGraphPolicyLogs
| where TimeGenerated > ago(24h)
| where AadTenantId == targetTenantId
| where RequestId == targetRequestId
| extend MatchingAssignments = toint(column_ifexists("EvaluatedPoliciesCount",
    column_ifexists("PolicyDetailsCount", int(null))))
| project TimeGenerated, RequestId, ClientRequestId, OperationId,
    RequestMethod, RequestUri, AppId, PolicyDecision,
    MatchingAssignments, ErrorPoliciesCount, PolicyDetails
```

`MatchingAssignments` uses the available count column. A null count means unknown, not zero; don't substitute the length of a potentially truncated `PolicyDetails` array.

For batch children, filter on the parent's `OperationId`; each child has its own `RequestId`. To correlate with [Graph activity logs](https://learn.microsoft.com/en-us/graph/microsoft-graph-activity-logs-overview), enable `MicrosoftGraphActivityLogs` separately and match `RequestId` and `OperationId`.

For a diagnostic checklist, see [Test and troubleshoot a resource policy](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-test-troubleshoot).

## Protect evaluation data

Limit access to exported logs and follow your organization's retention requirements. Don't put credentials or unnecessary personal data in policy messages.

## Related content

- [Analyze resource policy evaluation audit logs](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-logs).
- [How resource policy evaluation works](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-evaluation).
- [Safely deploy resource policy assignments](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-safe-deployment).
