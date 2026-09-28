<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecordingeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# callRecordingEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about call recording. This message is generated when a call recording starts.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callId | String | Unique identifier of the call. |
| callRecordingDisplayName | String | Display name for the call recording. |
| callRecordingDuration | Duration | Duration of the call recording. |
| callRecordingStatus | callRecordingStatus | Status of the call recording. The possible values are: `success`, `failure`, `initial`, `chunkFinished`, `unknownFutureValue`. |
| callRecordingUrl | String | Call recording URL. |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| meetingOrganizer | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Organizer of the meeting. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.callRecordingEventMessageDetail",
  "callId": "String",
  "callRecordingDisplayName": "String",
  "callRecordingDuration": "String (duration)",
  "callRecordingStatus": "String",
  "callRecordingUrl": "String",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "meetingOrganizer": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about call recording](https://learn.microsoft.com/en-us/graph/system-messages/#call-recording)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
