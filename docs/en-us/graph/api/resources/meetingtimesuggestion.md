<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingtimesuggestion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# meetingTimeSuggestion resource type

Namespace: microsoft.graph

A meeting suggestion that includes information like meeting time, attendance likelihood, individual availability, and available meeting locations.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "attendeeAvailability": [{"@odata.type": "microsoft.graph.attendeeAvailability"}],
  "confidence": 100.0,
  "locations": [{"@odata.type": "microsoft.graph.location"}],
  "meetingTimeSlot": {"@odata.type": "microsoft.graph.timeSlot"},
  "order": 1024,
  "organizerAvailability": "String",
  "suggestionReason": "String"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attendeeAvailability | [attendeeAvailability](https://learn.microsoft.com/en-us/graph/api/resources/attendeeavailability?view=graph-rest-1.0) collection | An array that shows the availability status of each attendee for this meeting suggestion. |
| confidence | Double | A percentage that represents the likelhood of all the attendees attending. |
| locations | [location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) collection | An array that specifies the name and geographic location of each meeting location for this meeting suggestion. |
| meetingTimeSlot | [timeSlot](https://learn.microsoft.com/en-us/graph/api/resources/timeslot?view=graph-rest-1.0) | A time period suggested for the meeting. |
| order | Int32 | Order of meeting time suggestions sorted by their computed confidence value from high to low, then by chronology if there are suggestions with the same confidence. |
| organizerAvailability | freeBusyStatus | Availability of the meeting organizer for this meeting suggestion. The possible values are: `free`, `tentative`, `busy`, `oof`, `workingElsewhere`, `unknown`. |
| suggestionReason | String | Reason for suggesting the meeting time. |
