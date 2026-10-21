<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementdatastatus -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# costManagementDataStatus resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Last modification time for the source data represented by a result.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `lastModifiedDateTime` | DateTimeOffset | When the underlying data was last modified, not when the request was received. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementDataStatus",
  "lastModifiedDateTime": "DateTimeOffset"
}
```
