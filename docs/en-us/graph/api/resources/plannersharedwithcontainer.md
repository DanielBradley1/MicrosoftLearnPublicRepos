<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannersharedwithcontainer?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-01-16 -->

# plannerSharedWithContainer resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the relationship of a Planner plan to a Planner container. Plans can be shared with containers that aren't the original container the plan belongs to. When the plan is verifying a user's access to it, the plan will additionally check the authorization logic of the containers it's shared with.

Inherits from [plannerPlanContainer](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontainer?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessLevel | plannerPlanAccessLevel | The maximum access level the shared container can provide to the plan. The possible values are: `readAccess`, `readWriteAccess`, `fullAccess`, `unknownFutureValue`. |
| containerId | String | The identifier of the resource that contains the plan. Optional. Inherited from [plannerPlanContainer](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontainer?view=graph-rest-beta). |
| type | plannerContainerType | The type of the resource that contains the plan. The possible values are: `group`, `unknownFutureValue`, `roster`, `project`, and `driveItem`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `roster`, `project`, `driveItem`. Optional. Inherited from [plannerPlanContainer](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontainer?view=graph-rest-beta). |
| url | String | The full canonical URL of the container. Optional. Inherited from [plannerPlanContainer](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontainer?view=graph-rest-beta). |

### plannerPlanAccessLevel values

| Member | Description |
| :--- | :--- |
| readAccess | The highest level of access that a user can gain through this relationship will be read access to the plan. |
| readWriteAccess | The highest level of access that a user can gain through this relationship will be read and write access to the plan. |
| fullAccess | The highest level of access that a user can gain through this relationship will be full access to the plan. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerSharedWithContainer",
  "url": "String",
  "containerId": "String",
  "type": "String",
  "accessLevel": "String"
}
```
