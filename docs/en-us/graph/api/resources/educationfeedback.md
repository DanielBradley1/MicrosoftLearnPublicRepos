<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationfeedback?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# educationFeedback resource type

Namespace: microsoft.graph

Feedback from a teacher to a student.

This property represents both the text part of the feedback along with who provided the feedback.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| feedbackBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | User who created the feedback. |
| feedbackDateTime | DateTimeOffset | Moment in time when the feedback was given. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| text | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Feedback. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "feedbackBy": {"@odata.type": "microsoft.graph.identitySet"},
  "feedbackDateTime": "String",
  "text": {"@odata.type": "microsoft.graph.itemBody"}
}
```
