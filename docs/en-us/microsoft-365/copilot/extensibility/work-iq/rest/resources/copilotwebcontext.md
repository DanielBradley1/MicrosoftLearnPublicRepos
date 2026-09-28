<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotwebcontext -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Work IQ - copilotWebContext resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

Determines how web search grounding is used in a Copilot conversation through the [Work IQ Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotroot-post-conversations).

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
