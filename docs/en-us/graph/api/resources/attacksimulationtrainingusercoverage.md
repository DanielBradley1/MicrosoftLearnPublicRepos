<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationtrainingusercoverage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# attackSimulationTrainingUserCoverage resource type

Namespace: microsoft.graph

Represents cumulative training data for a user in attack simulation and training.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get training coverage for users](https://learn.microsoft.com/en-us/graph/api/securityreportsroot-getattacksimulationtrainingusercoverage?view=graph-rest-1.0) | [attackSimulationTrainingUserCoverage](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationtrainingusercoverage?view=graph-rest-1.0) collection | List training coverage for tenant users in attack simulation and training campaigns. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attackSimulationUser | [attackSimulationUser](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationuser?view=graph-rest-1.0) | User in an attack simulation and training campaign. |
| userTrainings | [userTrainingStatusInfo](https://learn.microsoft.com/en-us/graph/api/resources/usertrainingstatusinfo?view=graph-rest-1.0) collection | List of assigned trainings and their statuses for the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attackSimulationTrainingUserCoverage",
  "attackSimulationUser": {
    "@odata.type": "microsoft.graph.attackSimulationUser"
  },
  "userTrainings": [
    {
      "@odata.type": "microsoft.graph.userTrainingStatusInfo"
    }
  ]
}
```
