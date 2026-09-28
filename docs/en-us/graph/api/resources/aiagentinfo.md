<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/aiagentinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-25 -->

# aiAgentInfo resource type

Namespace: microsoft.graph

Represents information about an AI agent that participated in the preparation of the message recorded in the [processConversationMetadata](https://learn.microsoft.com/en-us/graph/api/resources/processconversationmetadata?view=graph-rest-1.0) object.

Inherits from [aiInteractionEntity](https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionentity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blueprintId | String | The unique identifier of the [parent agent blueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint) that defines the identity and configuration of this agent instance. This identifier is provided by Microsoft Entra. |
| identifier | String | The unique identifier of this AI agent. Inherited from [aiInteractionEntity](https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionentity?view=graph-rest-1.0). This identifier is provided by the developer. If building on Microsoft Entra Agent ID, use the [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) ID. |
| name | String | The display name of the AI agent. Inherited from [aiInteractionEntity](https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionentity?view=graph-rest-1.0). |
| version | String | The version number of the AI agent used. Inherited from [aiInteractionEntity](https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionentity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.aiAgentInfo",
  "blueprintId": "String",
  "identifier": "String",
  "name": "String",
  "version": "String"
}
```
