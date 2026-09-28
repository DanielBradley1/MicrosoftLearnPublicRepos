<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/meetingnote -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# meetingNote resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a meeting note associated with a [call AI insight](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/callaiinsight).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `subpoints` | [meetingNoteSubpoint](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/meetingnotesubpoint) collection | A collection of subpoints of the meeting note. |
| `text` | String | The text of the meeting note. |
| `title` | String | The title of the meeting note. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.meetingNote",
  "subpoints": [{"@odata.type": "microsoft.graph.meetingNoteSubpoint"}],
  "text": "String",
  "title": "String"
}
```
