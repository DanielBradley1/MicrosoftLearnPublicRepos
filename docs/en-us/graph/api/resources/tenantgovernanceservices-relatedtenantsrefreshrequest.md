<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenantsrefreshrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# relatedTenantsRefreshRequest resource type

Namespace: microsoft.graph

Represents a request to [refresh related tenants](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-refresh?view=graph-rest-1.0) data outside the regular refresh schedule.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| location | String | The location URL where the status of the refresh request can be retrieved. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.relatedTenantsRefreshRequest",
  "location": "String"
}
```
