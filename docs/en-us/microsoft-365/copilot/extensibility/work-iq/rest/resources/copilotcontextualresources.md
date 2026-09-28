<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotcontextualresources -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Work IQ - copilotContextualResources resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

Optional contextual resources being sent into a Copilot conversation through the [Work IQ Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotroot-post-conversations).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `files` | [copilotFile](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotfile) collection | A collection of OneDrive and SharePoint file URIs that should be used as context when responding to the chat message. |
| `webContext` | [copilotWebContext](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotwebcontext) | Determines if web search grounding can be used to respond to the chat message. |

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
