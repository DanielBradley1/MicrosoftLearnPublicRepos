<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callstartedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# callStartedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about call started. This message is generated when a call starts.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callEventType | teamworkCallEventType | Represents the call event type. The possible values are: `call`, `meeting`, `screenShare`, `unknownFutureValue`. |
| callId | String | Unique identifier of the call. |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.callStartedEventMessageDetail",
  "callEventType": "String",
  "callId": "String",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about call started](https://learn.microsoft.com/en-us/graph/system-messages/#call-started)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
