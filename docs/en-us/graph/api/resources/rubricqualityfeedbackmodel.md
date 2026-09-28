<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/rubricqualityfeedbackmodel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# rubricQualityFeedbackModel resource type

Namespace: microsoft.graph

Feedback related to a specific [quality](https://learn.microsoft.com/en-us/graph/api/resources/rubricquality?view=graph-rest-1.0) of an [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| feedback | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Specific feedback for one quality of this rubric. |
| qualityId | String | The ID of the [rubricQuality](https://learn.microsoft.com/en-us/graph/api/resources/rubricquality?view=graph-rest-1.0) that this feedback is related to. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "feedback": {"@odata.type": "microsoft.graph.itemBody"},
  "qualityId": "String"
}
```
