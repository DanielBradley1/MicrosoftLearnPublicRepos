<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioplanreference?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# businessScenarioPlanReference resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a reference to a [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) object.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get plan](https://learn.microsoft.com/en-us/graph/api/businessscenarioplanner-getplan?view=graph-rest-beta) | [businessScenarioPlanReference](https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioplanreference?view=graph-rest-beta) | Get information about the [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) mapped to a given target. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the **plannerPlan**. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Read-only. |
| title | String | The title property of the **plannerPlan**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.businessScenarioPlanReference",
  "id": "String (identifier)",
  "title": "String"
}
```
