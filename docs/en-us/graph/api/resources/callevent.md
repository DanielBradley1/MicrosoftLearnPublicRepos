<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# callEvent resource type

Namespace: microsoft.graph

Contains information about a call event. The call can be a one-on-one or group ad-hoc call, a PSTN or VoIP call, or a scheduled active online meeting.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callEventType | callEventType | The event type of the call. The possible values are: `callStarted`, `callEnded`, `unknownFutureValue`, `rosterUpdated`. You must use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `rosterUpdated`. |
| eventDateTime | DateTimeOffset | The date and time when the event occurred. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The unique identifier for the call event. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| participants | [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-1.0) collection | Participants collection for the call event. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.callEvent",
  "callEventType": "String",
  "eventDateTime": "String (timestamp)",
  "id": "String (identifier)"
}
```

## Related content

- [Change notification for active meeting call events](https://learn.microsoft.com/en-us/graph/changenotifications-for-onlinemeeting)
