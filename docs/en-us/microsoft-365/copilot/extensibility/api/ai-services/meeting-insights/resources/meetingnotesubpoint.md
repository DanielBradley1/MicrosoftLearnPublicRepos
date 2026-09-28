<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/meetingnotesubpoint -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# meetingNoteSubpoint resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a meeting note subpoint associated with a [meeting note](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/meetingnote).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `text` | String | The text of the meeting note subpoint. |
| `title` | String | The title of the meeting note subpoint. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.meetingNoteSubpoint",
  "text": "String",
  "title": "String"
}
```
