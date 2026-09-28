<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/responsestatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# responseStatus resource type

Namespace: microsoft.graph

Represents the response status of an attendee or organizer for a meeting request.

You can get the response status of an attendee or organizer through the **responseStatus** property of an [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) or the **status** property of an [attendee](https://learn.microsoft.com/en-us/graph/api/resources/attendee?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| response | String | The response type. The possible values are: `none`, `organizer`, `tentativelyAccepted`, `accepted`, `declined`, `notResponded`.  <br>  <br>To differentiate between `none` and `notResponded`:  <br>  <br>`none` – from organizer's perspective. This value is used when the status of an attendee/participant is reported to the organizer of a meeting.  <br>  <br>`notResponded` – from attendee's perspective. Indicates the attendee has not responded to the meeting request.  <br>  <br>Clients can treat `notResponded` == `none`.  <br>  <br>As an example, if attendee Alex hasn't responded to a meeting request, getting Alex' response status for that event in Alex' calendar returns `notResponded`. Getting Alex' response from the calendar of any other attendee or the organizer's returns `none`. Getting the organizer's response for the event in anybody's calendar also returns `none`. |
| time | DateTimeOffset | The date and time when the response was returned. It uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "response": "String",
  "time": "String (timestamp)"
}
```
