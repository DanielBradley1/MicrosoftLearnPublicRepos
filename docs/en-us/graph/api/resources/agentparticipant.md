<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentparticipant?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# agentParticipant resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents another agent participating in an interaction with a protected agent.

Used in the **participants** property of [activityMetadata](https://learn.microsoft.com/en-us/graph/api/resources/activitymetadata?view=graph-rest-beta).

Inherits from [interactionParticipant](https://learn.microsoft.com/en-us/graph/api/resources/interactionparticipant?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | String | The Microsoft Entra application ID of the other agent. Inherited from [interactionParticipant](https://learn.microsoft.com/en-us/graph/api/resources/interactionparticipant?view=graph-rest-beta). Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentParticipant",
  "value": "String"
}
```
