<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/rubricquality?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# rubricQuality resource type

Namespace: microsoft.graph

A quality of a rubric.

See [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) for a description of the relationship between rubric *qualities*, *levels*, and *criteria*.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| criteria | [rubricCriterion](https://learn.microsoft.com/en-us/graph/api/resources/rubriccriterion?view=graph-rest-1.0) collection | The collection of criteria for this rubric quality. |
| description | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The description of this rubric quality. |
| displayName | String | The name of this rubric quality. |
| qualityId | String | The ID of this resource. |
| weight | Single | If present, a numerical weight for this quality. Weights must add up to 100. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "criteria": [{"@odata.type": "microsoft.graph.rubricCriterion"}],
  "description": {"@odata.type": "microsoft.graph.itemBody"},
  "displayName": "String",
  "qualityId": "String",
  "weight": "Double"
}
```
