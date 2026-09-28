<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tokenmeetinginfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# tokenMeetingInfo resource type

Namespace: microsoft.graph

This is the token information that allows you to join an existing meeting. This is obtained as part of the incoming call notification.

In the event that a call is disconnected, this information can help you rejoin that call.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| token | String | The token used to join the call. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "token": "String"
}
```
