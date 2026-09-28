<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/calltranscripteventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# callTranscriptEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about call transcript. This message is generated when transcript is available for a call.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callId | String | Unique identifier of the call. |
| callTranscriptICalUid | String | Unique identifier for a call transcript. |
| meetingOrganizer | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The organizer of the meeting. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.callTranscriptEventMessageDetail",
  "callId": "String",
  "callTranscriptICalUid": "String",
  "meetingOrganizer": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about call transcript](https://learn.microsoft.com/en-us/graph/system-messages/#call-transcript)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
