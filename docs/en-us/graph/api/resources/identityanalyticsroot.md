<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityanalyticsroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# identityAnalyticsRoot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a container for Microsoft Entra identity analytics in a tenant. Identity analytics reports point-in-time data about your directory objects, and currently covers the [groups](https://learn.microsoft.com/en-us/graph/api/resources/groupanalytics?view=graph-rest-beta) in the tenant.

Access this resource through the [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-beta) resource, at the `/reports/identityAnalytics` path.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| groups | [groupAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/groupanalytics?view=graph-rest-beta) collection | The analytics for the groups in the tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityAnalyticsRoot"
}
```
