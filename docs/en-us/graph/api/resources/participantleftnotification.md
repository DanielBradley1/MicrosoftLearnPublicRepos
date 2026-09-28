<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/participantleftnotification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# participantLeftNotification resource type

Namespace: microsoft.graph

Contains details about the policy-based participant who has left the call.

Under the [Policy-based recording](https://learn.microsoft.com/en-us/microsoftteams/teams-recording-policy) scenario, when a participant who is managed by the bot call has left the meeting, a `participantLeftNotification` will be sent to the bot to notify the bot with details of the participant left event.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| call | [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) | The call object that contains details about the participant joining event. |
| participantId | String | ID of the participant under the policy who has left the meeting. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "participantId": "String",
  "call": {"@odata.type": "#microsoft.graph.call"}
}
```
