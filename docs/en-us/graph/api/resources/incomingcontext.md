<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/incomingcontext?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# incomingContext resource type

Namespace: microsoft.graph

Represents the context associated with an incoming call.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| observedParticipantId | String | The ID of the participant that is under observation. Read-only. |
| onBehalfOf | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity that the call is happening on behalf of. |
| sourceParticipantId | String | The ID of the participant that triggered the incoming call. Read-only. |
| transferor | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity that transferred the call. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "sourceParticipantId": "String",
  "observedParticipantId": "String",
  "onBehalfOf": {"@odata.type": "#microsoft.graph.identitySet"},
  "transferor": {"@odata.type": "#microsoft.graph.identitySet"}
}
```
