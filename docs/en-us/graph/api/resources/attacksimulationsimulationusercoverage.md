<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationsimulationusercoverage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# attackSimulationSimulationUserCoverage resource type

Namespace: microsoft.graph

Represents cumulative simulation data and results for a user in attack simulation and training.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get simulation coverage for users](https://learn.microsoft.com/en-us/graph/api/securityreportsroot-getattacksimulationsimulationusercoverage?view=graph-rest-1.0) | [attackSimulationSimulationUserCoverage](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationsimulationusercoverage?view=graph-rest-1.0) collection | List [training coverage](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationtrainingusercoverage?view=graph-rest-1.0) for each tenant user in attack simulation and training campaigns. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attackSimulationUser | [attackSimulationUser](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationuser?view=graph-rest-1.0) | User in an attack simulation and training campaign. |
| clickCount | Int32 | Number of link clicks in the received payloads by the user in attack simulation and training campaigns. |
| compromisedCount | Int32 | Number of compromising actions by the user in attack simulation and training campaigns. |
| latestSimulationDateTime | DateTimeOffset | Date and time of the latest attack simulation and training campaign that the user was included in. |
| simulationCount | Int32 | Number of attack simulation and training campaigns that the user was included in. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attackSimulationSimulationUserCoverage",
  "attackSimulationUser": {
    "@odata.type": "microsoft.graph.attackSimulationUser"
  },
  "clickCount": "Int32",
  "compromisedCount": "Int32",
  "latestSimulationDateTime": "String (timestamp)",
  "simulationCount": "Int32"
}
```
