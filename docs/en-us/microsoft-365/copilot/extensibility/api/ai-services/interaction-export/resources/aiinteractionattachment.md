<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionattachment -->
<!-- Sitemap-Last-Modified: 2025-12-04 -->

# aiInteractionAttachment resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a message attachment, such as cards and images.

Note

For information about the AI interactions that are included with this API and the relevant licensing requirements, see [Licensing and prerequisites](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory#licensing-and-prerequisites) and [AI interactions returned](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory#ai-interactions-returned).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `attachmentId` | String | The identifier for the attachment. This identifier is only unique within the message scope. |
| `content` | String | The content of the attachment. |
| `contentType` | String | The type of the content. For example, `reference`, `file`, and `image/imageType`. |
| `contentUrl` | String | The URL of the content. |
| `name` | String | The name of the attachment. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "attachmentId": "String",
  "content": "String",
  "contentType": "String",
  "contentUrl": "String",
  "name": "String"
}
```
