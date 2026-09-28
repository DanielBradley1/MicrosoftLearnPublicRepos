<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingtimesuggestionsresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# meetingTimeSuggestionsResult resource type

Namespace: microsoft.graph

A collection of meeting suggestions if there is any, or the reason if there isn't.

The following are the possible reasons that [findMeetingTimes](https://learn.microsoft.com/en-us/graph/api/user-findmeetingtimes?view=graph-rest-1.0) does not return any meeting suggestions.

| **emptySuggestionsReason value** | **Reasons** |
| :--- | :--- |
| attendeesUnavailable | All of the attendees' availability is known, but not enough attendees are available to reach the [meeting confidence](https://learn.microsoft.com/en-us/graph/api/user-findmeetingtimes?view=graph-rest-1.0#the-confidence-of-a-meeting-suggestion) threshold, which is 50% by default, for any time period. |
| attendeesUnavailableOrUnknown | Some or all of the attendees have unknown availability, causing the meeting confidence to fall below the set threshold, which is 50% by default. Attendee availability can become unknown if the attendee is outside of the organization, or there is an error obtaining free/busy information. |
| locationsUnavailable | The **isRequired** property of the [locationConstraint](https://learn.microsoft.com/en-us/graph/api/resources/locationconstraint?view=graph-rest-1.0) parameter is specified as mandatory, and yet there are no locations available at the calculated time slots. |
| organizerUnavailable | The **isOrganizerOptional** parameter is false and yet the organizer is not available during the requested time window. |
| unknown | The reason for not returning any meeting suggestions is not known. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "emptySuggestionsReason": "String",
  "meetingTimeSuggestions": [{"@odata.type": "microsoft.graph.meetingTimeSuggestion"}]
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emptySuggestionsReason | String | A reason for not returning any meeting suggestions. The possible values are: `attendeesUnavailable`, `attendeesUnavailableOrUnknown`, `locationsUnavailable`, `organizerUnavailable`, or `unknown`. This property is an empty string if the **meetingTimeSuggestions** property does include any meeting suggestions. |
| meetingTimeSuggestions | [meetingTimeSuggestion](https://learn.microsoft.com/en-us/graph/api/resources/meetingtimesuggestion?view=graph-rest-1.0) collection | An array of meeting suggestions. |
