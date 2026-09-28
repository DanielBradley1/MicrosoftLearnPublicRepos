<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/aionlinemeeting -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# aiOnlineMeeting resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents an AI online meeting.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | The unique identifier for the AI online meeting. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `aiInsights` | [callAiInsight](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/callaiinsight) collection | A set of AI insights associated with an AI online meeting. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.aiOnlineMeeting",
  "id": "String (identifier)"
}
```
