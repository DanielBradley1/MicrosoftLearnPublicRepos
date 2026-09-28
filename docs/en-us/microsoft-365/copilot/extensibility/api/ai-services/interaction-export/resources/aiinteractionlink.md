<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionlink -->
<!-- Sitemap-Last-Modified: 2025-12-04 -->

# aiInteractionLink resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents the links that appear in an AI interaction.

Note

For information about the AI interactions that are included with this API and the relevant licensing requirements, see [Licensing and prerequisites](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory#licensing-and-prerequisites) and [AI interactions returned](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory#ai-interactions-returned).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `displayName` | String | The name of the link. |
| `linkType` | String | Information about a link in an app chat or Business Chat \(BizChat\) interaction. |
| `linkUrl` | String | The URL of the link. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "linkType": "String",
  "linkUrl": "String"
}
```
