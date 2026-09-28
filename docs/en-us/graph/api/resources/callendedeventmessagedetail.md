<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callendedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# callEndedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about an ended call. This message is generated when a call ends.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callDuration | Duration | Duration of the call. |
| callEventType | teamworkCallEventType | Represents the call event type. The possible values are: `call`, `meeting`, `screenShare`, `unknownFutureValue`. |
| callId | String | Unique identifier of the call. |
| callParticipants | [callParticipantInfo](https://learn.microsoft.com/en-us/graph/api/resources/callparticipantinfo?view=graph-rest-1.0) collection | List of call participants. |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.callEndedEventMessageDetail",
  "callDuration": "String (duration)",
  "callEventType": "String",
  "callId": "String",
  "callParticipants": [
    {
      "@odata.type": "microsoft.graph.callParticipantInfo"
    }
  ],
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about an ended call](https://learn.microsoft.com/en-us/graph/system-messages/#call-ended)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
