<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/overview -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Microsoft 365 Copilot Cost Management API overview

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

The Microsoft 365 Copilot Cost Management API helps administrators govern and observe tenant consumption of Copilot and AI **credits** through Microsoft Graph, rooted at `/copilot/costManagement`. The contract is unit-aware and credit-denominated. It covers the tenant credit balance snapshot, spending policy management, group audience scoping, per-service settings, notify-only threshold alerts and their recipients, per-user consumption balances, the review of users' credit requests, and usage reports that break down consumption by user, security group, governed service, and funding class.

The API is credit-denominated and deliberately excludes purchase forecasts. It doesn't return any currency, invoice, price, or settlement amounts.

## Key capabilities

- Read the tenant-wide credit balance snapshot, with one row per billing method.
- Create, read, update, and delete spending policies that cap Copilot Credits consumption for an audience.
- Scope a policy to every user in the tenant \(`allUsersSpendingPolicy`\) or to selected groups \(`selectedGroupsSpendingPolicy`\).
- Manage a policy's group audience through `$ref` reference links.
- Configure per-service settings that govern or exclude individual AI services within a policy.
- Configure notify-only threshold alerts and manage their recipients.
- Diagnose a user's per-service consumption balance and understand why a user can or can't consume a service.
- List, review, approve, or reject users' requests for Copilot credits, individually or in bulk.
- Report consumption for one completed UTC day by user, security group, and governed service, with ranking and paging.
- Report a calendar month's consumption by funding class \(prepaid, pay-as-you-go, unbilled overage, and non-billable\).
- Read one user's raw usage detail over a timestamp window, broken down by service and session.

## Example scenarios

- An administrator sets a monthly credit cap for a pilot group and alerts admins when usage reaches 80 percent.
- An administrator adds or removes a governed service on an existing policy.
- A support administrator diagnoses why a user can no longer consume a service by reading that user's per-service balance.
- A FinOps reader lists the tenant's enabled spending policies and reviews their configured limits.
- An AI administrator reviews pending credit requests for Work IQ and approves them in bulk.
- A FinOps analyst splits yesterday's consumption by service to see where credits went across AI experiences.
- A billing administrator closes a month by reviewing its consumption by funding class, including unbilled overage.
- A FinOps analyst or business unit lead ranks the highest-consuming users or security groups for a day.
- A support administrator inspects one user's raw usage sessions over a time window.

## Personas and roles

Target personas include the AI Administrator and License Administrator for policy management; the FinOps/Global Reader and Billing Administrator for reads; and the Support/Helpdesk administrator for per-user diagnostics. For usage reports, target personas include the FinOps analyst and Billing Administrator for the service and funding reports, and the FinOps analyst and business unit \(BU\) lead for the user and group rankings. Creating a spending policy also requires the Billing Administrator or Global Administrator directory role at runtime.

Billing Administrators, Global Administrators, AI Administrators, Global Readers, and AI Readers can read credit requests. Global Administrators, Billing Administrators, and AI Administrators can approve or reject them.

## Permissions

This API uses the `CopilotCostManagement-*` permission family. Most operations support only delegated \(work or school account\) permissions. The tenant credit balance read \([getTenantCreditBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementroot-gettenantcreditbalance)\) also supports the `CopilotCostManagement.Read.All` application permission, and the service and funding usage reports also support the `CopilotCostManagement-Reports.Read.All` and `CopilotCostManagement.Read.All` application permissions. Personal Microsoft accounts aren't supported. Choose the least privileged permission for each operation.

Important

Some Microsoft 365 Copilot Cost Management permissions might not yet appear in the API permission picker in the Microsoft Entra admin center. Normal administrator-consent and API authorization requirements still apply.

For delegated access, request the least-privileged permission listed for the operation by its fully qualified scope name in your app's authentication flow, for example `https://graph.microsoft.com/CopilotCostManagement-Reports.Read.All` for aggregate service or funding reports. An authorized tenant administrator can grant consent through a [tenant-specific administrator consent request](https://learn.microsoft.com/en-us/entra/identity-platform/v2-admin-consent#request-the-permissions-from-a-directory-admin) using your app's client ID, registered redirect URI, and the same scope name, without first selecting the permission in the picker.

This scope-name flow applies only to delegated permissions; it does not configure or grant application permissions.

| Permission | Operations |
| :--- | :--- |
| `CopilotCostManagement.Read.All` | Read the tenant credit balance snapshot. Also read all usage reports with delegated permissions. Application access applies only to the tenant credit balance and the service and funding usage reports. |
| `CopilotCostManagement-Reports.Read.All` | Read aggregate service and funding usage reports. |
| `CopilotCostManagement-Policy.Read.All` | Read spending policies, per-service settings, alert thresholds, and recipients. |
| `CopilotCostManagement-Policy.ReadWrite.All` | Create, update, and delete policies, service settings, alerts, and recipients. |
| `CopilotCostManagement-Assignment.Read.All` | Read a policy's group audience. |
| `CopilotCostManagement-Assignment.ReadWrite.All` | Add and remove a policy's group audience. |
| `CopilotCostManagement-UserData.Read.All` | Read a named user's balance diagnostics, including consumption and the selected `spendingPolicyId`. Also read user and group usage records and raw per-user usage detail, including services, sessions, native session identifiers, and first and last activity timestamps. |
| `CopilotCostManagement-CreditReq.Read.All` | Read credit requests. |
| `CopilotCostManagement-CreditReq.ReadWrite.All` | Read credit requests and approve or reject them. |

## API list

| Operation | HTTP method | Description |
| :--- | :--- | :--- |
| [Get tenant credit balance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementroot-gettenantcreditbalance) | GET `/copilot/costManagement/getTenantCreditBalance` | Get the tenant-wide credit balance snapshot. |
| [List spendingPolicies](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicy-list) | GET `/copilot/costManagement/spendingPolicies` | Get a list of spending policies. |
| [Create spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicy-create) | POST `/copilot/costManagement/spendingPolicies` | Create a new spending policy. |
| [Get spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicy-get) | GET `/copilot/costManagement/spendingPolicies/{id}` | Retrieve a spending policy. |
| [Update spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicy-update) | PATCH `/copilot/costManagement/spendingPolicies/{id}` | Update a spending policy. |
| [Delete spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicy-delete) | DELETE `/copilot/costManagement/spendingPolicies/{id}` | Delete a spending policy. |
| [List assignedGroups](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/selectedgroupsspendingpolicy-list-assignedgroups) | GET `/copilot/costManagement/spendingPolicies/{id}/microsoft.graph.selectedGroupsSpendingPolicy/assignedGroups` | List the groups assigned to a policy. |
| [Add assignedGroup](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/selectedgroupsspendingpolicy-post-assignedgroups) | POST `/copilot/costManagement/spendingPolicies/{id}/microsoft.graph.selectedGroupsSpendingPolicy/assignedGroups/$ref` | Add a group reference to a policy. |
| [Remove assignedGroup](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/selectedgroupsspendingpolicy-delete-assignedgroups) | DELETE `/copilot/costManagement/spendingPolicies/{id}/microsoft.graph.selectedGroupsSpendingPolicy/assignedGroups/{groupId}/$ref` | Remove a group reference. |
| [List spendingPolicyServiceSettings](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicyservicesetting-list) | GET `/copilot/costManagement/spendingPolicies/{id}/serviceSettings` | List the service settings of a policy. |
| [Create spendingPolicyServiceSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicyservicesetting-create) | POST `/copilot/costManagement/spendingPolicies/{id}/serviceSettings` | Add a service to a policy. |
| [Get spendingPolicyServiceSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicyservicesetting-get) | GET `/copilot/costManagement/spendingPolicies/{id}/serviceSettings/{serviceId}` | Retrieve a service setting. |
| [Update spendingPolicyServiceSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicyservicesetting-update) | PATCH `/copilot/costManagement/spendingPolicies/{id}/serviceSettings/{serviceId}` | Update a service setting. |
| [Get costManagementAlertSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-get) | GET `/copilot/costManagement/spendingPolicies/{id}/emailThresholdSettings` | Retrieve the alert configuration of a policy. |
| [Update costManagementAlertSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-update) | PATCH `/copilot/costManagement/spendingPolicies/{id}/emailThresholdSettings` | Create or update the alert configuration. |
| [Delete costManagementAlertSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-delete) | DELETE `/copilot/costManagement/spendingPolicies/{id}/emailThresholdSettings` | Delete the alert configuration. |
| [List recipients](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-list-recipients) | GET `/copilot/costManagement/spendingPolicies/{id}/emailThresholdSettings/recipients` | List the alert recipients. |
| [Add recipient](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-post-recipients) | POST `/copilot/costManagement/spendingPolicies/{id}/emailThresholdSettings/recipients/$ref` | Add an alert recipient. |
| [Remove recipient](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-delete-recipients) | DELETE `/copilot/costManagement/spendingPolicies/{id}/emailThresholdSettings/recipients/{userId}/$ref` | Remove an alert recipient. |
| [Get costManagementUserBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserbalance-get) | GET `/copilot/costManagement/userBalances/{userId}` | Retrieve a user's consumption balance. |
| [List costManagementUserServiceBalances](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserservicebalance-list) | GET `/copilot/costManagement/userBalances/{userId}/serviceBalances` | List a user's per-service balance rows. |
| [Get costManagementUserServiceBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserservicebalance-get) | GET `/copilot/costManagement/userBalances/{userId}/serviceBalances/{serviceId}` | Retrieve one service's balance row for a user. |
| [List creditRequests](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-list) | GET `/copilot/costManagement/creditRequests` | List the tenant's credit requests. |
| [Get creditRequest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-get) | GET `/copilot/costManagement/creditRequests/{id}` | Retrieve a credit request. |
| [Update creditRequest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-update) | PATCH `/copilot/costManagement/creditRequests/{id}` | Approve or reject a credit request. |
| [Batch record decisions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-batchrecorddecisions) | POST `/copilot/costManagement/creditRequests/batchRecordDecisions` | Approve or reject credit requests in bulk. |
| [List costManagementUserUsageRecords](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagerecord-list) | GET `/copilot/costManagement/usageReports/userUsageRecords` | List reported consumption per user for one completed UTC day. |
| [Get costManagementUserUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagerecord-get) | GET `/copilot/costManagement/usageReports/userUsageRecords/{userId}` | Retrieve one user's reported consumption for one completed UTC day. |
| [List costManagementGroupUsageRecords](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementgroupusagerecord-list) | GET `/copilot/costManagement/usageReports/groupUsageRecords` | List reported consumption per security group for one completed UTC day. |
| [Get costManagementGroupUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementgroupusagerecord-get) | GET `/copilot/costManagement/usageReports/groupUsageRecords/{groupId}` | Retrieve one security group's reported consumption for one completed UTC day. |
| [List costManagementServiceUsageRecords](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementserviceusagerecord-list) | GET `/copilot/costManagement/usageReports/serviceUsageRecords` | List reported consumption per governed service for one completed UTC day. |
| [Get costManagementServiceUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementserviceusagerecord-get) | GET `/copilot/costManagement/usageReports/serviceUsageRecords/{serviceId}` | Retrieve one service's reported consumption for one completed UTC day. |
| [List costManagementFundingUsageRecords](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementfundingusagerecord-list) | GET `/copilot/costManagement/usageReports/fundingUsageRecords` | List reported consumption per funding class for a calendar month. |
| [Get costManagementUserUsageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagedetail-get) | GET `/copilot/costManagement/usageReports/userUsageDetails/{userId}` | Retrieve one user's raw usage detail over a timestamp window. |
| [List costManagementUserUsageServiceDetails](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusageservicedetail-list) | GET `/copilot/costManagement/usageReports/userUsageDetails/{userId}/services` | List one user's raw consumption by governed service. |
| [List costManagementUserUsageSessionDetails](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagesessiondetail-list) | GET `/copilot/costManagement/usageReports/userUsageDetails/{userId}/sessions` | List one user's raw usage grouped by session. |

## Concurrency and removal semantics

- To mutate an existing policy and its child resources \(service settings and reference links\), include an `If-Match` header with the parent policy's ETag. Service settings and reference links don't have their own ETag. The parent policy manages concurrency and appears as `parentEtag` on a service setting. When you create a policy, it has no existing ETag and doesn't use `If-Match`.
- The `serviceSettings` collection doesn't support `DELETE`. Set `state` to `disabled` to remove a service. The entry stays in that state.
- Manage the `assignedGroups` and `recipients` relationships as reference navigation properties with `$ref` add and remove.
- Credit requests carry their own strong ETag, returned as `@odata.etag` and in the `ETag` response header. [Update creditRequest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-update) requires an `If-Match` header; the [batchRecordDecisions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-batchrecorddecisions) action takes a per-item `etag` instead.
- A credit request decision that matches the current state is a no-op that preserves the ETag, `decisionBy`, and timestamps. The ETag is still checked, so a same-state decision with a stale ETag fails with `preconditionFailed`.
- Credit requests can't be created or deleted through the API. Users create them outside Microsoft Graph, and the service retains them according to its retention policy.

## Usage report time selectors and paging

Usage reports live under `/copilot/costManagement/usageReports`. Every usage report request requires a time selector, supplied as query parameters. Requests without the required selectors are rejected with a `400 unsupportedQuery` response.

| Selector family | Parameters | Format | Used by |
| :--- | :--- | :--- | :--- |
| Completed UTC day | `startDate`, `endDate` | Date, `YYYY-MM-DD`. Inclusive start and exclusive end. `endDate` must equal `startDate` plus one day, and its UTC midnight must not be later than the current time. | User, group, and service usage records \(list and get\) |
| Calendar month | `month` | String, `YYYY-MM`. Date ranges are rejected. | Funding usage records |
| Timestamp window | `startDateTime`, `endDateTime` | DateTimeOffset, UTC ISO 8601, up to seven fractional digits. Inclusive start and exclusive end. Currently, `startDateTime` must be earlier than `endDateTime`, `endDateTime` can't be later than the current time, the window can be at most 24 hours long, and the window can't cross a UTC calendar-month boundary. The end can equal midnight UTC on the first day of the next month. | User usage detail, and its services and sessions |

Invalid selectors are rejected, not clamped. Current-day, future, and multi-day ranges on the completed-UTC-day reports return a `400` response, as do timestamp windows that currently don't meet the timestamp-window limits in the table. Validation doesn't enforce an oldest permitted `startDate` or `month`.

- **Paging.** The user, group, and service usage records and the user usage sessions use server-driven paging with `$skiptoken`; `$skip` isn't supported. Follow the complete `@odata.nextLink` URL unchanged. The continuation keeps the original selectors, filter, and order, but it isn't a point-in-time snapshot. Later pages read current data, so rows can repeat or be missed between pages. A `nextLink` whose dates differ from the original request is rejected with a `400` response. On the user, group, and service usage records, `$top` accepts an integer from 1 through 100 with a default of 10, and values outside that range are rejected, not capped. The user usage sessions have a separate default page size of 20 and a maximum of 100. Funding usage records and the user usage services aren't paged.
- **Filtering.** The user, group, and service usage records support `$filter` on `userId`, `groupId`, and `serviceId` respectively, by using only the `eq` operator. Other operators, such as `in`, aren't supported.
- **Ordering.** Only `consumedQuantity` supports `$orderby`. Ties are broken internally, and ordering on the dimension key isn't supported.
- **Units.** Every quantity carries a `unit`, currently `copilotCredit`. No currency, invoice, price, or settlement amounts are returned.
- **Processed versus raw.** `userUsageRecords` returns processed consumption for one completed UTC day that you can rank across users. `userUsageDetails` returns one user's raw, billable-flagged usage over a timestamp window, with service and session breakdowns. The two measurements, including their `sessionCount` values, aren't guaranteed to be equal.
- **Not-readable parents.** `GET /copilot/costManagement/usageReports` returns a `404` response and carries no data. `GET /copilot/costManagement/usageReports/userUsageDetails` isn't listable; read the detail by user ID instead.

## Error conditions

Error responses use the standard OData `error` and `innerError` envelope. The `innerError.code` reports workload-specific conditions, while the standard OData `error.code` reports generic conditions. Row-level security runs before lookup, so an out-of-scope tenant resource returns a `404` response instead of a `403` response.

| Condition | HTTP | Error code |
| :--- | :--- | :--- |
| Caller lacks the required permission or a qualifying directory role | 403 | `Authorization_RequestDenied` |
| Unsupported query option or malformed request | 400 | `invalidRequest`, `unsupportedQuery` |
| Usage report time selector is missing, malformed, or incompatible; a user, group, or service range doesn't select exactly one completed UTC day; `$top` on the user, group, or service usage records is outside 1 through 100; a user usage detail window's start isn't earlier than its end, its end is later than the current time, it's longer than 24 hours, or it crosses a UTC calendar-month boundary; or a continuation token is invalid or mismatched | 400 | `unsupportedQuery` |
| A keyed usage report read has no represented usage. This response isn't proof of zero consumption or of whether the user or group exists. | 404 | `usageDataUnavailable` |
| Removing the last assigned group would leave the policy with no assigned audience | 409 | `lastAssignedGroup` |
| Another non-disabled tenant-wide policy already governs the same service | 409 | `allUsersServiceConflict` |
| A group-scoped policy shares both an assigned group and an enabled service with another non-disabled policy | 409 | `groupServiceConflict` |
| Disabling the last enabled service on a policy that has service settings | 409 | `atLeastOneServiceRequired` |
| Alert threshold value out of range \(percentage thresholds must be an integer 1-100\) | 400 | `invalidAlertThreshold` |
| PATCHing any field on a policy that isn't in an editable state | 400 | `policyNotEditableWhilePending` |
| Unknown or invalid service ID | 400 | `invalidService` |
| Alerting enabled with no recipient linked, or removing the last recipient while alerting is enabled | 400 | `alertRecipientsRequired` |
| Alert recipient reference doesn't resolve to a real user in the tenant directory | 400 | `alertRecipientNotFound` |
| Supplying a server-managed field on PATCH | 400 | `invalidRequest` |
| Stale `If-Match` on a mutating operation | 412 | `preconditionFailed` |
| Missing `If-Match` on a credit request update | 428 | `preconditionRequired` |
| Malformed, weak \(`W/`\), or `*` `If-Match` on a credit request update | 400 | `invalidRequest` |
| Conflicting concurrent state transition | 409 | `invalidTransition` |
| Upstream evaluator failed for every service, so no balance row could be produced | 503 | `sourceUnavailable` |
| Credit request ID doesn't exist | 404 | `itemNotFound` |
| Invalid bulk decision payload, such as an empty list, more than 100 items, or duplicate request IDs | 400 | `invalidRequest` |
| Unsupported credit request state transition on update | 400 | `invalidRequest` |
| Credit request list or count dependency failure | 503 | `serviceNotAvailable` |
| Usage report source failed. Don't treat this response as zero consumption. | 503 | `sourceUnavailable` |
| API throttling. Honor the `Retry-After` header. | 429 | `tooManyRequests` |

The [batchRecordDecisions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-batchrecorddecisions) action returns per-item failures in a `200 OK` response, not as HTTP errors.

## Related content

- [spendingPolicy resource type](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy)
- [costManagementUserBalance resource type](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserbalance)
- [creditRequest resource type](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequest)
- [costManagementUsageReportRoot resource type](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementusagereportroot)
- [costManagementUserUsageRecord resource type](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagerecord)
