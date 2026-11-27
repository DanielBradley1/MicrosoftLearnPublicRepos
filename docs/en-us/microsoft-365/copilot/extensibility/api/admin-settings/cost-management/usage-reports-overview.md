<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/usage-reports-overview -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# Microsoft 365 Copilot usage reports overview

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Use the [Cost Management API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/overview) usage reports to analyze consumption of Copilot Credits by user, security group, governed service, or funding class. You can also inspect one user's raw usage by service and session.

All reports are under `/copilot/costManagement/usageReports`. Every request requires a time selector. Each quantity includes a `unit`, currently `copilotCredit`; reports don't return currency, invoice, price, or settlement amounts.

Note

The [usage report root](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementusagereportroot) organizes the report collections but doesn't return a report itself. `GET /copilot/costManagement/usageReports` returns a `404` response. Call a report operation instead.

## Choose a report

Choose a daily report to compare consumption across users, groups, or services, a monthly report to review funding, or raw detail to investigate one user's activity.

| Report | Use it to | Operations |
| :--- | :--- | :--- |
| [User usage record](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagerecord) | Compare or rank users' processed consumption for one completed UTC day. | [List user records](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagerecord-list), [Get user record](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagerecord-get) |
| [Group usage record](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementgroupusagerecord) | Compare security groups' consumption for one completed UTC day. | [List group records](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementgroupusagerecord-list), [Get group record](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementgroupusagerecord-get) |
| [Service usage record](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementserviceusagerecord) | Compare governed services' share of tenant consumption for one completed UTC day. | [List service records](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementserviceusagerecord-list), [Get service record](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementserviceusagerecord-get) |
| [Funding usage record](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementfundingusagerecord) | Review a calendar month's consumption by funding class, including unbilled consumption. | [List funding records](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementfundingusagerecord-list) |
| [User usage detail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagedetail) | Inspect one user's raw, billable-flagged usage over a timestamp window. | [Get user detail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagedetail-get), [List service details](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusageservicedetail-list), [List session details](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagesessiondetail-list) |

### Understand user usage detail

User usage detail contains two breakdowns of the same user's raw activity:

- [Service detail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusageservicedetail) splits consumption by governed service. This breakdown isn't the tenant-wide daily service report.
- [Session detail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagesessiondetail) groups activity by native session identifier. Activity without a session identifier might be omitted, so session quantities might not sum to the parent detail's `consumedQuantity`.

Read the parent detail by user ID. The API doesn't support listing the parent collection: `GET /copilot/costManagement/usageReports/userUsageDetails` returns a `404` response. You can expand `services` or `sessions` on the parent, or list them through their own endpoints with the same timestamp window. For complete session paging, use [List session details](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagesessiondetail-list).

Processed user usage records and raw user usage detail aren't interchangeable. Their consumption measurements and `sessionCount` values might not match. To diagnose whether a user can currently consume a service, use [user balances](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserbalance) instead of a usage report.

## Permissions

Choose the least privileged permission for the operation. The following table describes the Graph permission model. For deployment requirements, see [permission availability and authorization](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/overview#permission-availability-and-authorization). Personal Microsoft accounts aren't supported.

| Reports | Least privileged permission | Access in the Graph permission model |
| :--- | :--- | :--- |
| User records, group records, and raw user detail, including services and sessions | `CopilotCostManagement-UserData.Read.All` | Delegated work or school account, or application |
| Service records and funding records | `CopilotCostManagement-Reports.Read.All` | Delegated work or school account, or application |

`CopilotCostManagement.Read.All` is a higher privileged alternative for all usage report GET operations in both access schemes. Both the granular permissions and the broad permission require administrator consent. For consent guidance, see [Cost Management API permissions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/overview#permissions). Check each operation's reference for its permission requirements.

## Time selectors

Time selectors are required query parameters, not `$filter` expressions. Use the selector family for the report you choose. Missing, malformed, or incompatible selectors return `400 unsupportedQuery`. The API rejects invalid ranges instead of adjusting them.

| Reports | Required parameters | Format |
| :--- | :--- | :--- |
| User, group, and service usage records, for both list and get | `startDate`, `endDate` | `YYYY-MM-DD` |
| Funding usage records | `month` | `YYYY-MM` |
| User usage detail and its services and sessions | `startDateTime`, `endDateTime` | UTC ISO 8601 timestamps, with up to seven fractional digits |

### Completed UTC day

For user, group, and service usage records, `startDate` is inclusive and `endDate` is exclusive. `endDate` must equal `startDate` plus one day, and its UTC midnight can't be later than the current time. The API rejects current-day, future, and multi-day ranges.

For example, `startDate=2026-07-01&endDate=2026-07-02` selects July 1, 2026, after that UTC day finishes. Validation doesn't enforce an oldest permitted `startDate`.

### Calendar month

Funding usage records use a UTC calendar month, such as `month=2026-07`, rather than a date range. The API rejects date ranges. Validation doesn't enforce an oldest permitted `month`.

### Timestamp window

For user usage detail and its services and sessions, the window includes `startDateTime` and excludes `endDateTime`. Currently:

- `startDateTime` must be earlier than `endDateTime`.
- `endDateTime` can't be later than the current time.
- The window can be at most 24 hours long.
- The window can't cross a UTC calendar-month boundary. Because the end is exclusive, it can equal midnight UTC on the first day of the next month.

For example, `2026-07-31T00:00:00Z` through `2026-08-01T00:00:00Z` is a valid window after its end time has passed.

## Paging

Paging support varies by collection.

| Collection | Paging | Page size |
| :--- | :--- | :--- |
| User, group, and service usage records | Server-driven, using `@odata.nextLink` and `$skiptoken` | `$top` accepts 1 through 100; default 10. Values outside this range are rejected, not capped. |
| User usage sessions | Server-driven, using `@odata.nextLink` and `$skiptoken` | Default 20; maximum 100. Supports `$top`. |
| Funding usage records and user usage services | Not paged | The complete result is returned. `$top` isn't supported. |

`$top` is an upper bound, not a guaranteed page size. Follow the complete `@odata.nextLink` URL unchanged; don't construct offsets or change its time selectors. `$skip` isn't supported.

A continuation keeps the original selectors and any supported filter and order, but it isn't a point-in-time snapshot. Later pages read current data, so rows can repeat or be missed between pages. Invalid or mismatched continuation tokens return `400 unsupportedQuery`.

When you expand `sessions` on a user usage detail, the response can include `sessions@odata.nextLink`. Follow that link for more rows, or call [List session details](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagesessiondetail-list) directly.

## Filtering and ordering

The following options apply to **list operations**, not to every request under the usage report root. All these list operations support `$select`.

| Collection | `$filter` | `$orderby` | `$count` |
| :--- | :--- | :--- | :--- |
| User usage records | `userId eq 'value'` only | `consumedQuantity asc` or `consumedQuantity desc` | Supported |
| Group usage records | `groupId eq 'value'` only | `consumedQuantity asc` or `consumedQuantity desc` | Supported |
| Service usage records | `serviceId eq 'value'` only | `consumedQuantity asc` or `consumedQuantity desc` | Supported |
| Funding usage records | Not supported | `consumedQuantity asc` or `consumedQuantity desc` | Supported |
| User usage services | Not supported | Not supported | Not supported |
| User usage sessions | Not supported | Not supported | Not supported |

The daily record filters support only `eq`, not `in` or other operators. Ordering on dimension keys such as `userId` isn't supported. Ties in `consumedQuantity` are broken internally.

To customize a [Get user usage detail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagedetail-get) request, use `$select` or `$expand` on `services` and `sessions`. That operation doesn't support `$filter`, `$orderby`, `$top`, or `$count`. Check each method reference for its complete query-option contract.

## Interpret results and errors

When a report exposes `dataStatus`, use [costManagementUsageDataStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementusagedatastatus) to understand source freshness. Its `latestSourceDateTime` doesn't guarantee that a result is complete or that the covered period has closed. For raw user detail, `dataStatus` can be `null` when the source has no as-of timestamp to report. Don't interpret `null` as an error or as the current time.

| Response | Meaning |
| :--- | :--- |
| `400 unsupportedQuery` | The request uses invalid or missing time selectors, unsupported query options, an invalid daily-record `$top` value, or an invalid or mismatched continuation token. |
| `404 usageDataUnavailable` | A keyed report read has no represented usage. This condition isn't proof of zero consumption or of whether a user or group exists. |
| `503 sourceUnavailable` | The usage source failed. Don't treat the response as zero consumption. |

An out-of-scope resource also returns `404`. For common authorization and throttling errors, see [Cost Management API error conditions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/overview#error-conditions).

## Related content

- [Cost Management API overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/overview)
- [Usage report root resource type](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementusagereportroot)
- [User balance resource type](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserbalance)
