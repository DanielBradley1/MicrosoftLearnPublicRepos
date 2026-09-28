<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/resources/copilotcontextualresources -->
<!-- Sitemap-Last-Modified: 2025-10-17 -->

# copilotContextualResources resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Optional contextual resources being sent into a Copilot conversation through the [Microsoft 365 Copilot Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/copilotroot-post-conversations).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `files` | [copilotFile](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/resources/copilotfile) collection | A collection of OneDrive and SharePoint file URIs that should be used as context when responding to the chat message. |
| `webContext` | [copilotWebContext](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/resources/copilotwebcontext) | Determines if web search grounding can be used to respond to the chat message. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotContextualResources",
  "files": [
    {
      "@odata.type": "#microsoft.graph.copilotFile"
    }
  ],
  "webContext": {
    "@odata.type": "#microsoft.graph.copilotWebContext"
  }
}
```
