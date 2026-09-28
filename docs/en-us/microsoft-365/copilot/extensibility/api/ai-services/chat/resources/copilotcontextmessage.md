<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/resources/copilotcontextmessage -->
<!-- Sitemap-Last-Modified: 2025-10-17 -->

# copilotContextMessage resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents extra context for a Copilot conversation through the [Microsoft 365 Copilot Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/copilotroot-post-conversations).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `description` | String | The description of the additional context. |
| `text` | String | The text of the additional context. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotContextMessage",
  "text": "String",
  "description": "String"
}
```
