<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/resources/aiuser -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# aiUser resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents an AI user or agent.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | The unique identifier for the AI user. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `interactionHistory` | [aiInteractionHistory](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory) | The history of interactions between AI agents and users. |

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `interactionHistory` | [aiInteractionHistory](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory) | The history of interactions between AI agents and users. |
| `onlineMeetings` | [aiOnlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/aionlinemeeting) collection | Information about an online meeting, including AI insights. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)"
}
```
