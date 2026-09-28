<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotcontextmessage -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Work IQ - copilotContextMessage resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

Represents extra context for a Copilot conversation through the [Work IQ Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotroot-post-conversations).

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
