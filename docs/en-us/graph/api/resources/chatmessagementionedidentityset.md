<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessagementionedidentityset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-16 -->

# chatMessageMentionedIdentitySet resource type

Namespace: microsoft.graph

Represents the resource \(user, application, or conversation\) @mentioned in a [message](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) in a chat or a channel.

Inherits from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| application | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Inherited from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0). If present, represents an application \(for example, bot\) @mentioned in a [message](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| conversation | [teamworkConversationIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkconversationidentity?view=graph-rest-1.0) | If present, represents a conversation \(for example, team, channel, or chat\) @mentioned in a [message](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| device | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Inherited from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0). Not used because it's not supported to @mention devices. |
| user | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Inherited from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0). If present, represents a user @mentioned in a [message](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.chatMessageMentionedIdentitySet",
  "application": {
    "@odata.type": "microsoft.graph.identity"
  },
  "conversation": {
    "@odata.type": "microsoft.graph.teamworkConversationIdentity"
  },
  "device": {
    "@odata.type": "microsoft.graph.identity"
  },
  "user": {
    "@odata.type": "microsoft.graph.identity"
  }
}
```
