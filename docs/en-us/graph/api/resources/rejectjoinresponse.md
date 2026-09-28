<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/rejectjoinresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# rejectJoinResponse resource type

Namespace: microsoft.graph

Contains a response to reject a participant who tries to join the meeting.

This has the same effect as rejecting a policy recording incoming call notification using the [reject-call](https://learn.microsoft.com/en-us/graph/api/call-reject?view=graph-rest-1.0) method. The bot will continue to receive a participant joining notification for a new user joining until its capacity has been reached.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| reason | String | The rejection reason. Possible values are `None`, `Busy`, and `Forbidden`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "reason": "None | Busy | Forbidden" 
}
```
