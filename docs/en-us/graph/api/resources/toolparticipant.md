<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/toolparticipant?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# toolParticipant resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a tool participating in an interaction with a protected agent.

Used in the **participants** property of [activityMetadata](https://learn.microsoft.com/en-us/graph/api/resources/activitymetadata?view=graph-rest-beta).

Inherits from [interactionParticipant](https://learn.microsoft.com/en-us/graph/api/resources/interactionparticipant?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mcpServerId | String | The stable identifier of the Model Context Protocol \(MCP\) server that hosts the tool. Optional. |
| value | String | The stable identifier assigned to the tool by the agent platform. Inherited from [interactionParticipant](https://learn.microsoft.com/en-us/graph/api/resources/interactionparticipant?view=graph-rest-beta). Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.toolParticipant",
  "mcpServerId": "String",
  "value": "String"
}
```
