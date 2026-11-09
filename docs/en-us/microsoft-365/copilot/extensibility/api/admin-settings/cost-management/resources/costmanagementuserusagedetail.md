<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagedetail -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# costManagementUserUsageDetail resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

One user's raw, billable-flagged consumption of Copilot Credits over a required `startDateTime` and `endDateTime` timestamp window, bounded to the latest processed watermark rather than reprocessed. The detail is keyed on `userId`.

This resource is distinct from [costManagementUserUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagerecord). A user usage record is a processed, date-bounded report for one completed UTC day that can be ranked across users. A user usage detail is raw, timestamp-bounded, and read for one user at a time. The `sessionCount` values of the two resources aren't guaranteed to be equal.

Note

The parent collection `GET /copilot/costManagement/usageReports/userUsageDetails` isn't listable and returns a `404` response. Read a detail by the user's identifier instead.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagedetail-get) | [costManagementUserUsageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagedetail) | Retrieve the properties and relationships of a costManagementUserUsageDetail object. |
| [List services](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusageservicedetail-list) | [costManagementUserUsageServiceDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusageservicedetail) collection | Get the user's raw consumption by governed service. |
| [List sessions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagesessiondetail-list) | [costManagementUserUsageSessionDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagesessiondetail) collection | Get the user's raw usage grouped by native session identifier. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `consumedQuantity` | Double | Raw, billable-flagged consumption attributed to this user over the requested window, bounded to the latest processed watermark rather than reprocessed. Read-only. |
| `dataStatus` | [costManagementUsageDataStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementusagedatastatus) | Freshness of the source activity data this detail was computed from, when the source reports an as-of timestamp for the window. `null` when the source has none to report; don't treat `null` as an error or as the current time. Read-only. |
| `sessionCount` | Int64 | Count of billable-flagged activity sessions, bounded to the latest processed watermark, that contributed to `consumedQuantity`. Excludes non-billable activity. Read-only. |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | Unit that applies to `consumedQuantity`. Read-only. |
| `userId` | String | The identifier of the user this detail covers. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `services` | [costManagementUserUsageServiceDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusageservicedetail) collection | This user's raw consumption, split by governed service. Supports `$expand`. Returns the complete result for the window and isn't paged. |
| `sessions` | [costManagementUserUsageSessionDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagesessiondetail) collection | This user's raw usage grouped by session identifiers represented by the native source. Supports `$expand`. Activity without a session identifier might be omitted, and child quantities need not sum to `consumedQuantity`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementUserUsageDetail",
  "consumedQuantity": "Double",
  "dataStatus": {
    "@odata.type": "microsoft.graph.costManagementUsageDataStatus"
  },
  "sessionCount": "Int64",
  "unit": "String",
  "userId": "String"
}
```
