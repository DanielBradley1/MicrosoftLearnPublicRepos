<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/resources/copilotwebcontext -->
<!-- Sitemap-Last-Modified: 2025-10-17 -->

# copilotWebContext resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Determines how web search grounding is used in a Copilot conversation through the [Microsoft 365 Copilot Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/copilotroot-post-conversations).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `isWebEnabled` | Boolean | Determines if web search grounding is enabled or not when responding to the current chat message. By default, web search grounding is enabled. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotWebContext",
  "isWebEnabled": "Boolean"
}
```
