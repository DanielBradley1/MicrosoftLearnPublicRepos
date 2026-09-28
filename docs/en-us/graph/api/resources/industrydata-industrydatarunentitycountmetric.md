<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunentitycountmetric?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# industryDataRunEntityCountMetric resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the measure of total, active, and inactive entries for a single entity.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| active | Int32 | The count of entries for the entity marked as `Active`. |
| inactive | Int32 | The count of entries for the entity marked as `Inactive`. |
| total | Int32 | Total count of the entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.industryDataRunEntityCountMetric",
  "active": "Int32",
  "inactive": "Int32",
  "total": "Int32"
}
```
