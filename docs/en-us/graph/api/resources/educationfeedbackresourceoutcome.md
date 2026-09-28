<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationfeedbackresourceoutcome?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# educationFeedbackResourceOutcome resource type

Namespace: microsoft.graph

Represents feedback on an [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) object in the form of a document.

Inherits from [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Add submission feedback resource outcome](https://learn.microsoft.com/en-us/graph/api/educationfeedbackresourceoutcome-post-outcomes?view=graph-rest-1.0) | [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) | Create a new [feedback resource](https://learn.microsoft.com/en-us/graph/api/resources/educationfeedbackresourceoutcome?view=graph-rest-1.0) for a submission. |
| [Delete feedback resource outcome](https://learn.microsoft.com/en-us/graph/api/educationfeedbackresourceoutcome-delete?view=graph-rest-1.0) | None | Delete a [feedback resource](https://learn.microsoft.com/en-us/graph/api/resources/educationfeedbackresourceoutcome?view=graph-rest-1.0) from a submission. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| feedbackResource | [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0) | The actual feedback resource. |
| id | String | Unique identifier for the **educationFeedbackResourceOutcome**. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The individual who updated the resource. Inherited from [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The moment in time when the resource was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2021 is `2021-01-01T00:00:00Z`. Inherited from [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0). |
| resourceStatus | educationFeedbackResourceOutcomeStatus | The status of the feedback resource. The possible values are: `notPublished`, `pendingPublish`, `published`, `failedPublish`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "feedbackResource": {"@odata.type": "microsoft.graph.educationResource"},
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "resourceStatus": {"@odata.type": "microsoft.graph.educationFeedbackResourceOutcomeStatus"}
}
```
