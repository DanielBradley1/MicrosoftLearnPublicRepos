<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenantsrefreshstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# relatedTenantsRefreshStatus resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the [status](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-refreshstatus?view=graph-rest-beta) of a [related tenants refresh operation](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-refreshstatus?view=graph-rest-beta), including the most recent refresh timestamp and current status of the operation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mostRecentRefreshTime | String | Timestamp of the respective refresh request. |
| mostRecentRefreshRequestStatus | String | The status of the refresh operation |
| isFirstRefresh | Boolean | Describes whether the related tenants refresh was the initial aggregation done by our service or not. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.relatedTenantsRefreshStatus",
  "mostRecentRefreshTime": "String",
  "mostRecentRefreshRequestStatus": "String",
  "isFirstRefresh": "Boolean"
}
```
