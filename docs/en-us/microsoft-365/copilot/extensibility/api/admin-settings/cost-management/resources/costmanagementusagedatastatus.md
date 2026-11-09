<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementusagedatastatus -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# costManagementUsageDataStatus resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Freshness of the source data behind a usage report result that can report it. Used by [costManagementFundingUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementfundingusagerecord) and [costManagementUserUsageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagedetail). This type is distinct from [costManagementDataStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementdatastatus), which reports when the underlying data was last modified.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `latestSourceDateTime` | DateTimeOffset | Timestamp of the latest source event or snapshot sync incorporated into the result. Its meaning depends on the operation: the snapshot sync time for funding usage records, and the source enqueue watermark for raw user usage detail. It doesn't indicate that the result is complete or that the covered period has closed; a later read over the same window can return a later value or more rows. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementUsageDataStatus",
  "latestSourceDateTime": "DateTimeOffset"
}
```
