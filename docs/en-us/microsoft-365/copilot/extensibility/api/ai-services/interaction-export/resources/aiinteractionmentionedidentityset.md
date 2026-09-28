<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionmentionedidentityset -->
<!-- Sitemap-Last-Modified: 2025-12-04 -->

# aiInteractionMentionedIdentitySet resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents an entity mentioned in an AI interaction.

Inherits from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset).

Note

For information about the AI interactions that are included with this API and the relevant licensing requirements, see [Licensing and prerequisites](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory#licensing-and-prerequisites) and [AI interactions returned](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory#ai-interactions-returned).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `conversation` | [teamworkConversationIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkconversationidentity) | The conversation details. |
| `tag` | [teamworkTagIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagidentity) | The tag details. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "conversation": {"@odata.type": "microsoft.graph.teamworkConversationIdentity"},
  "tag": {"@odata.type": "microsoft.graph.teamworkTagIdentity"}
}
```
