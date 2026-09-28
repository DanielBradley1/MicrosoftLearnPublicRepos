<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingparticipants?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# meetingParticipants resource type

Namespace: microsoft.graph

Represents participants in a meeting.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attendees | [meetingParticipantInfo](https://learn.microsoft.com/en-us/graph/api/resources/meetingparticipantinfo?view=graph-rest-1.0) collection | Information about the meeting attendees. |
| organizer | [meetingParticipantInfo](https://learn.microsoft.com/en-us/graph/api/resources/meetingparticipantinfo?view=graph-rest-1.0) | Information about the meeting organizer. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "attendees": [{"@odata.type": "#microsoft.graph.meetingParticipantInfo"}],
  "organizer": {"@odata.type": "#microsoft.graph.meetingParticipantInfo"}
}
```
