<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/invitationparticipantinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# invitationParticipantInfo resource type

Namespace: microsoft.graph

This resource is used to represent the entity that is being invited to a group call.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hidden | Boolean | Optional. Whether to hide the participant from the roster. |
| identity | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) associated with this invitation. |
| participantId | String | Optional. The ID of the target participant. |
| removeFromDefaultAudioRoutingGroup | Boolean | Optional. Whether to remove them from the main mixer. |
| replacesCallId | String | Optional. The call which the target identity is currently a part of. For peer-to-peer case, the call will be dropped once the participant is added successfully. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "identity": {"@odata.type": "#microsoft.graph.identitySet"},
  "participantId": "String",  
  "replacesCallId": "String",
  "removeFromDefaultAudioRoutingGroup": "Boolean",
  "hidden": "Boolean"
}
```
