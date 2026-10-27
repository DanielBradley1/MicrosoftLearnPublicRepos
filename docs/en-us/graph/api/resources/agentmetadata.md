<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentmetadata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# agentMetadata resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents metadata used to identify and evaluate an agent for data loss prevention \(DLP\) policies.

Configured in the **agentMetadata** property of [policyLocationAgent](https://learn.microsoft.com/en-us/graph/api/resources/policylocationagent?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agentAdministrativeUnitId | String | The identifier of the administrative unit associated with the agent. Optional. |
| agentBlueprintId | String | The identifier of the blueprint from which the agent was created. Optional. |
| agentCategory | String | The category of the agent, for example, `Agents.Foundry.MicrosoftAzure`, `Agents.Copilot.Studio`, or `Agents.Local`. Optional. |
| agentOwner | String | The owner associated with the agent. Optional. |
| agentPublisher | String | The publisher associated with the agent. Optional. |
| altAgentIds | String collection | Alternate identifiers that can identify the agent. Required when **agentMetadata** is provided. Use an empty collection \(`[]`\) when the agent has no alternate identifiers. |
| isEntraAgentId | Boolean | Indicates whether the **value** property of the associated [policyLocationAgent](https://learn.microsoft.com/en-us/graph/api/resources/policylocationagent?view=graph-rest-beta) is a Microsoft Entra agent ID. Required when **agentMetadata** is provided. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentMetadata",
  "agentAdministrativeUnitId": "String",
  "agentBlueprintId": "String",
  "agentCategory": "String",
  "agentOwner": "String",
  "agentPublisher": "String",
  "altAgentIds": [
    "String"
  ],
  "isEntraAgentId": "Boolean"
}
```
