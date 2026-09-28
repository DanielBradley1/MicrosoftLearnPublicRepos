<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/emergencycallevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# emergencyCallEvent resource type

Namespace: microsoft.graph

Contains information about an emergency call event.

Inherits from [callEvent](https://learn.microsoft.com/en-us/graph/api/resources/callevent?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callerInfo | [emergencyCallerInfo](https://learn.microsoft.com/en-us/graph/api/resources/emergencycallerinfo?view=graph-rest-1.0) | The information of the emergency caller. |
| callEventType | callEventType | The event type of the call. The possible values are: `callStarted`, `callEnded`, `unknownFutureValue`, `rosterUpdated`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `rosterUpdated`. Inherited from [callEvent](https://learn.microsoft.com/en-us/graph/api/resources/callevent?view=graph-rest-1.0). |
| emergencyNumberDialed | String | The emergency number dialed. |
| eventDateTime | DateTimeOffset | The date and time when the event occurred. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [callEvent](https://learn.microsoft.com/en-us/graph/api/resources/callevent?view=graph-rest-1.0). |
| id | String | The unique identifier of the **emergencyCallEvent** object. Inherited from [callEvent](https://learn.microsoft.com/en-us/graph/api/resources/callevent?view=graph-rest-1.0). |
| policyName | String | The policy name for the emergency call event. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| participants | [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-1.0) collection | This navigation property exists for consistency with the base type, but isn't defined for emergency call events. Inherited from [microsoft.graph.callEvent](https://learn.microsoft.com/en-us/graph/api/resources/callevent?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.emergencyCallEvent",
  "callerInfo": {"@odata.type": "microsoft.graph.emergencyCallerInfo"},
  "callEventType": "String",
  "emergencyNumberDialed": "String",
  "eventDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "policyName": "String"
}
```

## Related content

- [Change notification for emergency call events](https://learn.microsoft.com/en-us/graph/changenotifications-for-emergencycalls)
