<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-timelineevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# timelineEvent resource type

Namespace: microsoft.graph.security

The timeline of an [analyzedEmail](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| eventDateTime | DateTimeOffset | The date and time when the event occurred. |
| eventDetails | String | Additional details or context about the event. |
| eventResult | String | The outcome or result of the event, such as delivery location or action taken. |
| eventSource | [microsoft.graph.security.eventSource](#eventsource-values) | The origin or actor that triggered the event. The possible values are: `system`, `admin`, `user`, `unknownFutureValue`. |
| eventThreats | String collection | Collection of threats identified or associated with this event. |
| eventType | [microsoft.graph.security.timelineEventType](#timelineeventtype-values) | The type of event that occurred. The possible values are: `originalDelivery`, `systemTimeTravel`, `dynamicDelivery`, `userUrlClick`, `reprocessed`, `zap`, `quarantineRelease`, `air`, `unknown`, `unknownFutureValue`. |

### eventSource values

| Member |
| :--- |
| system |
| admin |
| user |
| unknownFutureValue |

### timelineEventType values

| Member |
| :--- |
| originalDelivery |
| systemTimeTravel |
| dynamicDelivery |
| userUrlClick |
| reprocessed |
| zap |
| quarantineRelease |
| air |
| unknown |
| unknownFutureValue |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.timelineEvent",
  "eventDateTime": "String (timestamp)",
  "eventSource": "String",
  "eventType": "String",
  "eventResult": "String",
  "eventThreats": [
    "String"
  ],
  "eventDetails": "String"
}
```
