<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingquestionassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-14 -->

# bookingQuestionAssignment resource type

Namespace: microsoft.graph

Contains the set of custom questions associated with a particular service.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isRequired | Boolean | Indicates whether it's mandatory to answer the custom question. |
| questionId | String | The ID of the custom question. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bookingQuestionAssignment",
  "isRequired": "Boolean",
  "questionId": "String"
}
```
