<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/mentionevent -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# mentionEvent resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a mention event associated with a [callAiInsightViewPoint](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/callaiinsightviewpoint).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `eventDateTime` | DateTimeOffset | The date and time of the mention event. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| `speaker` | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The speaker who mentioned the user. |
| `transcriptUtterance` | String | The utterance in the online meeting transcript that contains the mention event. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mentionEvent",
  "eventDateTime": "String (timestamp)",
  "speaker": {"@odata.type": "microsoft.graph.identitySet"},
  "transcriptUtterance": "String"
}
```
