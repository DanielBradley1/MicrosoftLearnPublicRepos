<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationrepeatoffender?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# attackSimulationRepeatOffender resource type

Namespace: microsoft.graph

Represents a user in a tenant who has given way to attacks more than once across various attack simulation and training campaigns.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get repeat offenders](https://learn.microsoft.com/en-us/graph/api/securityreportsroot-getattacksimulationrepeatoffenders?view=graph-rest-1.0) | [attackSimulationRepeatOffender](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationrepeatoffender?view=graph-rest-1.0) collection | List the tenant users who have yielded to attacks more than once in attack simulation and training campaigns. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attackSimulationUser | [attackSimulationUser](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationuser?view=graph-rest-1.0) | The user in an attack simulation and training campaign. |
| repeatOffenceCount | Int32 | Number of repeat offences of the user in attack simulation and training campaigns. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attackSimulationRepeatOffender",
  "attackSimulationUser": {
    "@odata.type": "microsoft.graph.attackSimulationUser"
  },
  "repeatOffenceCount": "Int32"
}
```
