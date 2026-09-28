<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/securityreportsroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# securityReportsRoot resource type

Namespace: microsoft.graph

Represents an abstract type that contains resources for attack simulation and training reports. This resource provides the ability to launch a realistic simulated phishing attack that organizations can learn from.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get simulation coverage for users](https://learn.microsoft.com/en-us/graph/api/securityreportsroot-getattacksimulationsimulationusercoverage?view=graph-rest-1.0) | [attackSimulationSimulationUserCoverage](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationsimulationusercoverage?view=graph-rest-1.0) collection | List [training coverage](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationtrainingusercoverage?view=graph-rest-1.0) for each tenant user in attack simulation and training campaigns. |
| [Get training coverage for users](https://learn.microsoft.com/en-us/graph/api/securityreportsroot-getattacksimulationtrainingusercoverage?view=graph-rest-1.0) | [attackSimulationTrainingUserCoverage](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationtrainingusercoverage?view=graph-rest-1.0) collection | List training coverage for tenant users in attack simulation and training campaigns. |
| [Get repeat offenders](https://learn.microsoft.com/en-us/graph/api/securityreportsroot-getattacksimulationrepeatoffenders?view=graph-rest-1.0) | [attackSimulationRepeatOffender](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationrepeatoffender?view=graph-rest-1.0) collection | List the tenant users who have yielded to attacks more than once in attack simulation and training campaigns. |

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.securityReportsRoot",
}
```
