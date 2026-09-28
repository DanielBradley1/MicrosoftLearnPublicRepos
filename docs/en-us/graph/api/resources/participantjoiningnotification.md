<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/participantjoiningnotification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# participantJoiningNotification resource type

Namespace: microsoft.graph

Contains details about the policy-based participant joining a call.

Under the [Policy-based recording scenario](https://learn.microsoft.com/en-us/microsoftteams/teams-recording-policy), before a participant under the policy joins a call, a `participantJoiningNotification` will be sent to the bot associated with the policy that has available capacity to handle the new participant.

A [participantJoiningResponse](https://learn.microsoft.com/en-us/graph/api/resources/participantjoiningresponse?view=graph-rest-1.0) in the response payload is expected from the bot.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| call | [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) | The call object that contains details about the participant joining event. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "call": {"@odata.type": "#microsoft.graph.call"}
}
```
