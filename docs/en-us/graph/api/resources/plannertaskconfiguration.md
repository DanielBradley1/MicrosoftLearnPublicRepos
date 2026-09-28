<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# plannerTaskConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the configuration of [plannerTasks](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta) created for a [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/plannertaskconfiguration-get?view=graph-rest-beta) | [plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta) | Read the properties and relationships of a [plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/plannertaskconfiguration-update?view=graph-rest-beta) | [plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta) | Update the properties of a [plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| editPolicy | [plannerTaskPolicy](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskpolicy?view=graph-rest-beta) | Policy configuration for tasks created for the businessScenario when they're being changed outside of the scenario. |
| id | String | The unique identifier for the task configuration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskConfiguration",
  "editPolicy": {"@odata.type": "microsoft.graph.plannerTaskPolicy"},
  "id": "String (identifier)"
}
```
