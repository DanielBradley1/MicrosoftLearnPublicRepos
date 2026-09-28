<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioplanner?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# businessScenarioPlanner resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains Microsoft Planner-related content for the scenario, allowing both configuration of Planner behavior and accessing the scenario data in Planner.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get businessScenarioPlanner](https://learn.microsoft.com/en-us/graph/api/businessscenarioplanner-get?view=graph-rest-beta) | [businessScenarioPlanner](https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioplanner?view=graph-rest-beta) | Read the properties and relationships of a [businessScenarioPlanner](https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioplanner?view=graph-rest-beta) object. |
| [getPlan](https://learn.microsoft.com/en-us/graph/api/businessscenarioplanner-getplan?view=graph-rest-beta) | [businessScenarioPlanReference](https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioplanreference?view=graph-rest-beta) | Get information about the [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) mapped to a given target. |
| [Get plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/plannerplanconfiguration-get?view=graph-rest-beta) | [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) | Get the **plannerPlanConfiguration** from the **planConfiguration** navigation property. |
| [Get plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/plannertaskconfiguration-get?view=graph-rest-beta) | [plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta) | Get the **plannerTaskConfiguration** from the **taskConfiguration** navigation property. |
| [List tasks](https://learn.microsoft.com/en-us/graph/api/businessscenarioplanner-list-tasks?view=graph-rest-beta) | [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) collection | Get the **businessScenarioTasks** from the **tasks** navigation property. |
| [Create businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/businessscenarioplanner-post-tasks?view=graph-rest-beta) | [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) | Create a new **businessScenarioTask** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the **businessScenarioPlanner** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| planConfiguration | [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) | The configuration of Planner plans that will be created for the scenario. |
| taskConfiguration | [plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta) | The configuration of Planner tasks that will be created for the scenario. |
| tasks | [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) collection | The Planner tasks for the scenario. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.businessScenarioPlanner",
  "id": "String (identifier)"
}
```
