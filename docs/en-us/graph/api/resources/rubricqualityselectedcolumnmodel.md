<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/rubricqualityselectedcolumnmodel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# rubricQualitySelectedColumnModel resource type

Namespace: microsoft.graph

Indicates the [rubricLevel](https://learn.microsoft.com/en-us/graph/api/resources/rubriclevel?view=graph-rest-1.0) selected by the teacher when grading an [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| columnId | String | ID of the selected level for this quality. |
| qualityId | String | ID of the associated quality. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "columnId": "String",
  "qualityId": "String"
}
```
