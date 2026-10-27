<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenantsrefreshstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# relatedTenantsRefreshStatus resource type

Namespace: microsoft.graph

Represents the status of the most recent [related tenants refresh operation](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-refresh?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isFirstRefresh | Boolean | Indicates whether the operation is the first refresh of the related tenants list. |
| mostRecentRefreshDateTime | DateTimeOffset | The date and time of the most recent refresh operation. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. |
| mostRecentRefreshRequestStatus | String | The status of the most recent refresh operation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.relatedTenantsRefreshStatus",
  "isFirstRefresh": "Boolean",
  "mostRecentRefreshDateTime": "String (timestamp)",
  "mostRecentRefreshRequestStatus": "String"
}
```
