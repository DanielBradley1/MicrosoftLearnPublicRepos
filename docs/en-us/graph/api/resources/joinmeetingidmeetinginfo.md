<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/joinmeetingidmeetinginfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# joinMeetingIdMeetingInfo resource type

Namespace: microsoft.graph

Contains information that allows you to join an existing meeting with a **joinMeetingId** and a **passcode** \(if required\). You can retrieve these properties from the [Get onlineMeeting](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-get?view=graph-rest-1.0) API.

Inherits from [meetingInfo](https://learn.microsoft.com/en-us/graph/api/resources/meetinginfo?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| joinMeetingId | String | The ID used to join the meeting. |
| passcode | String | The passcode used to join the meeting. Optional. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "joinMeetingId": "String",
    "passcode": "String"
}
```
