<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/joinmeetingidsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# joinMeetingIdSettings resource type

Namespace: microsoft.graph

Specifies the **joinMeetingId**, the meeting passcode, and the requirement for the passcode for an online meeting.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isPasscodeRequired | Boolean | Indicates whether a passcode is required to join a meeting when using **joinMeetingId**. Optional. |
| joinMeetingId | String | The meeting ID to be used to join a meeting. Optional. Read-only. |
| passcode | String | The passcode to join a meeting. Optional. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.joinMeetingIdSettings",
  "isPasscodeRequired": "Boolean",
  "joinMeetingId": "String",
  "passcode": "String"
}
```
