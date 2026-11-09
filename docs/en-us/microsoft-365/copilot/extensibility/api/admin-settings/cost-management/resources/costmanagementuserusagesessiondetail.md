<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagesessiondetail -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# costManagementUserUsageSessionDetail resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A native-source session grouping within a user's raw usage detail, contained by [costManagementUserUsageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagedetail). Activity without a session identifier might be omitted from the session breakdown, even when it contributes to the parent total. Reading a single session row by key \(`GET .../sessions/{id}`\) isn't supported.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagesessiondetail-list) | [costManagementUserUsageSessionDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagesessiondetail) collection | Get a list of costManagementUserUsageSessionDetail objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `consumedQuantity` | Double | Raw, billable-flagged consumption attributed to this session grouping within the containing user's detail window. Session rows need not sum to the parent's `consumedQuantity`. Read-only. |
| `firstActivityDateTime` | DateTimeOffset | Time the earliest activity in this session was recorded, or `null` when the source didn't report one. Read-only. |
| `id` | String | Opaque identifier of this row, scoped to the containing user's detail and stable across repeated reads of the same request. It isn't a global or persistent session identifier, and it's distinct from `sourceSessionId`. Read-only. |
| `lastActivityDateTime` | DateTimeOffset | Time the latest activity in this session was recorded, or `null` when the source didn't report one. Read-only. |
| `sourceSessionId` | String | The native session identifier returned by the source, preserved verbatim, including `null` if the source returns it. Distinct from this row's opaque `id`. Read-only. |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | Unit that applies to `consumedQuantity`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementUserUsageSessionDetail",
  "consumedQuantity": "Double",
  "firstActivityDateTime": "DateTimeOffset",
  "id": "String",
  "lastActivityDateTime": "DateTimeOffset",
  "sourceSessionId": "String",
  "unit": "String"
}
```
