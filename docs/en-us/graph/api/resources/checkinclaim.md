<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# checkInClaim resource type

Namespace: microsoft.graph

Represents the check-in status to a place for an Outlook calendar event.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/place-post-checkins?view=graph-rest-1.0) | [checkInClaim](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0) | Create a new [checkInClaim](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0) object to record the check-in status for a specific place, such as a [desk](https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0), [room](https://learn.microsoft.com/en-us/graph/api/resources/room?view=graph-rest-1.0), or [workspace](https://learn.microsoft.com/en-us/graph/api/resources/workspace?view=graph-rest-1.0), associated with a specific calendar reservation. |
| [Get](https://learn.microsoft.com/en-us/graph/api/checkinclaim-get?view=graph-rest-1.0) | [checkInClaim](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0) | Read the properties and relationships of a [checkInClaim](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| calendarEventId | String | The unique identifier for an Outlook calendar event associated with the **checkInClaim** object. For more information, see the **iCalUId** property in [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0). |
| checkInMethod | [checkInMethod](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0#checkinmethod-values) | Indicates the method of check-in. The possible values are: `unspecified`, `manual`, `inferred`, `verified`, `unknownFutureValue`. The default value is `unspecified`. |
| createdDateTime | DateTimeOffset | The date and time when the **checkInClaim** object was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

### checkInMethod values

| Member | Description |
| :--- | :--- |
| unspecified | Default value when no other check-in method is used. We recommend that you use a value other than `unspecified`. |
| manual | Manual check-in to a desk or room based on an email or Teams chat reminder. |
| inferred | Check-in based on wireless network, badge access, or GPS signal. |
| verified | Check-in via a device bound to a place. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.checkInClaim",
  "calendarEventId": "String (identifier)",
  "checkInMethod": "String",
  "createdDateTime": "String (timestamp)"
}
```
