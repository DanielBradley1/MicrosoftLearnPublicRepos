<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-userfeedback?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# userFeedback resource type

Namespace: microsoft.graph.callRecords

Represents the feedback provided by the user an endpoint about the quality of the session.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| rating | microsoft.graph.callRecords.userFeedbackRating | The rating provided by the user of this endpoint about the quality of this Session. The possible values are: `notRated`, `bad`, `poor`, `fair`, `good`, `excellent`, `unknownFutureValue`. |
| text | String | The feedback text provided by the user of this endpoint for the session. |
| tokens | [microsoft.graph.callRecords.feedbackTokenSet](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-feedbacktokenset?view=graph-rest-1.0) | The set of feedback tokens provided by the user of this endpoint for the session. This is a set of Boolean properties. The property names should not be relied upon since they may change depending on what tokens are offered to the user. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "rating": "String",
  "text": "String",
  "tokens": {"@odata.type": "microsoft.graph.callRecords.feedbackTokenSet"}
}
```
