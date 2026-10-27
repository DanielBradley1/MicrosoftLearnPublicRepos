<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/interactionparticipant?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# interactionParticipant resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents another participant in an agent interaction. This type is abstract. Use the **@odata.type** property to specify an [agentParticipant](https://learn.microsoft.com/en-us/graph/api/resources/agentparticipant?view=graph-rest-beta), [toolParticipant](https://learn.microsoft.com/en-us/graph/api/resources/toolparticipant?view=graph-rest-beta), or [userParticipant](https://learn.microsoft.com/en-us/graph/api/resources/userparticipant?view=graph-rest-beta).

Used in the **participants** property of [activityMetadata](https://learn.microsoft.com/en-us/graph/api/resources/activitymetadata?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | String | The identifier of the participant. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.interactionParticipant",
  "value": "String"
}
```
