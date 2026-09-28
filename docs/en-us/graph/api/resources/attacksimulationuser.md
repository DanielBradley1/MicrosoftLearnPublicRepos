<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# attackSimulationUser resource type

Namespace: microsoft.graph

Represents a user in an attack simulation and training campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the user. |
| email | String | Email address of the user. |
| userId | String | This is the **id** property value of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) resource that represents the user in the Microsoft Entra tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attackSimulationUser",
  "displayName": "String",
  "email": "String",
  "userId": "String"
}
```
