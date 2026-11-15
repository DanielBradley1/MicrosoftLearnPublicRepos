<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# agentInfo resource type

Namespace: microsoft.graph

Describes the agent recorded in the **agent** property of an [agentRun](https://learn.microsoft.com/en-us/graph/api/resources/agentrun?view=graph-rest-beta). This embedded complex type isn't an independently addressable resource.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationId | String | The agent's Microsoft Entra application identifier, when available. |
| definitionName | String | The qualified agent definition name, when available. Not an addressable catalog link. |
| displayName | String | The agent's display name, when available. |
| key | String | The opaque identifier of the recorded agent instance. A structural property, not an OData entity key. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentInfo",
  "key": "String",
  "displayName": "String",
  "definitionName": "String",
  "applicationId": "String"
}
```
