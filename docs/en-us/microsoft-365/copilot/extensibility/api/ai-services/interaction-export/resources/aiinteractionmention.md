<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionmention -->
<!-- Sitemap-Last-Modified: 2025-12-04 -->

# aiInteractionMention resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a mention of an entity in an AI interaction.

Note

For information about the AI interactions that are included with this API and the relevant licensing requirements, see [Licensing and prerequisites](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory#licensing-and-prerequisites) and [AI interactions returned](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory#ai-interactions-returned).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `mentioned` | [aiInteractionMentionedIdentitySet](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionmentionedidentityset) | The entity mentioned in the message. |
| `mentionId` | Int32 | The identifier for the mention. |
| `mentionText` | String | The text mentioned in the message. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "mentioned": {"@odata.type": "microsoft.graph.AiInteractionMentionedIdentitySet"},
  "mentionId": "Int32",
  "mentionText": "String"
}
```
