<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-basicfilter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# basicFilter resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A basic filter implementation with single condition on a single attribute.

Inherits from [microsoft.graph.industryData.filter](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-filter?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attribute | microsoft.graph.industryData.filteroptions | The attribute to filter on. The possible values are: `orgExternalId`, `unknownFutureValue`. |
| in | String collection | The condition to filter with. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.basicFilter",
  "attribute": "String",
  "in": ["String"]
}
```
