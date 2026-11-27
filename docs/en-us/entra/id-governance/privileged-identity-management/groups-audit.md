<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/groups-audit -->
<!-- Sitemap-Last-Modified: 2026-04-23 -->

# Audit activity history for group assignments in Privileged Identity Management

## Overview

When working with your organization's groups in Privileged Identity Management \(PIM\), you can view activity, activations, and audit history for Microsoft Entra group membership or ownership changes.

Note

If your organization has outsourced management functions to a service provider who uses [Azure Lighthouse](https://learn.microsoft.com/en-us/azure/lighthouse/overview), role assignments authorized by that service provider won't be shown here.

Follow these steps to view the audit history for groups in Privileged Identity Management.

## View resource audit history

**Resource audit** gives you a view of all activity associated with groups in PIM.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator).
2. Browse to **ID Governance** > **Privileged Identity Management** > **Groups**.
3. Select the group you want to view audit history for.
4. Select **Resource audit**.

   [![Screenshot of where to select Resource audit.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-for-groups/pim-group-19.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-for-groups/pim-group-19.png#lightbox)
5. Filter the history using a predefined date or custom range.

## View my audit

**My audit** enables you to view your personal role activity for groups in PIM.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **ID Governance** > **Privileged Identity Management** > **Groups**.
3. Select the group you want to view audit history for.
4. Select **My audit**.

   [![Screenshot of where to select My audit.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-for-groups/pim-group-20.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-for-groups/pim-group-20.png#lightbox)
5. Filter the history using a predefined date or custom range.

## Correlate events related to the same activation cycle

`CorrelationId` is generally used to correlate audit log events related to one request. With PIM, multiple asynchronously processed operations can be part of one activation/deactivation cycle. As a result, some events related to the same activation/deactivation cycle will have different `CorrelationId`s.

### Correlate activation events

During group membership/ownership activation, the following operations might be processed asynchronously, resulting in multiple `CorrelationId`s being generated:

- **Scheduled activation**: Eligible users can schedule group membership/ownership activation for a future time. PIM tracks the request and automatically creates the group membership or ownership assignment at the scheduled time without further user input. This asynchronous operation generates a new `CorrelationId` at activation, which might differ from the original request's `CorrelationId`. This makes correlating the request and activation by `CorrelationId` difficult.
- **Approval-gated activation**: When PIM policy requires approval, an eligible user creates an activation request, and a designated approver approves it. PIM then assigns group membership or ownership immediately or at the user's scheduled start time. Because this flow is asynchronous, the `CorrelationId` might differ across stages.
- In rare cases, `CorrelationId` might change during the group membership/ownership activation flow due to the way requests are processed between systems.

Use `roleAssignmentRequestId` to correlate events related to one activation request in these scenarios. `roleAssignmentRequestId` remains the same during the asynchronous processing of operations such as scheduled activation or approval.

Use the following example Log Analytics query to get audit log entries related to group membership/ownership activation:

```Kusto
AuditLogs
| where OperationName has "Add member to role"
```

Use the output of this query to get the `roleAssignmentRequestId` for the event you need to analyze.

Use the following example Log Analytics query to get audit log entries related to the same group membership/ownership activation:

```Kusto
let roleAssignmentRequestId = "{roleAssignmentRequestId}";
AuditLogs
| where AdditionalDetails has roleAssignmentRequestId
```

### Correlate deactivation events

`CorrelationId` logged during the deactivation process depends on how deactivation was triggered:

- When deactivation is triggered automatically based on the expiration of an activated group membership or ownership assignment, `CorrelationId` of deactivation events matches the latest `CorrelationId` used during the activation.
- When deactivation is triggered by the assignee \(user selected **Deactivate** on the portal\), `CorrelationId` will be different from the one used in the activation flow.

In both cases, `roleAssignmentRequestId` of the original activation request is logged under **Additional details** for audit log events of deactivation.

Use the following example Log Analytics query to get audit log entries related to the full activation/deactivation cycle:

```Kusto
let roleAssignmentRequestId = "{roleAssignmentRequestId}";
let relatedCorrelationIds = AuditLogs
   | where AdditionalDetails has roleAssignmentRequestId
   | summarize makeset(CorrelationId);
AuditLogs
| where AdditionalDetails has roleAssignmentRequestId
  or CorrelationId in (relatedCorrelationIds)
```

## Next steps

- [Assign eligibility for a group in Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/groups-assign-member-owner)
