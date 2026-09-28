<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/callaiinsightviewpoint -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# callAiInsightViewPoint resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents user-specific properties of a [call AI insight](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/callaiinsight). These properties might differ based on who calls the API.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `mentionEvents` | [mentionEvent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/mentionevent) collection | The collection of AI-generated mention events. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.callAiInsightViewPoint",
  "mentionEvents": [{"@odata.type": "microsoft.graph.mentionEvent"}]
}
```
