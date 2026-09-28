<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerplandetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# plannerPlanDetails resource type

Namespace: microsoft.graph

Represents the additional information about a plan. Each [plan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) object has a details object.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get plan details](https://learn.microsoft.com/en-us/graph/api/plannerplandetails-get?view=graph-rest-1.0) | [plannerPlanDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannerplandetails?view=graph-rest-1.0) | Read properties and relationships of **plannerPlanDetails** object. |
| [Update plan details](https://learn.microsoft.com/en-us/graph/api/plannerplandetails-update?view=graph-rest-1.0) | [plannerPlanDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannerplandetails?view=graph-rest-1.0) | Update **plannerPlanDetails** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| categoryDescriptions | [plannerCategoryDescriptions](https://learn.microsoft.com/en-us/graph/api/resources/plannercategorydescriptions?view=graph-rest-1.0) | An object that specifies the descriptions of the 25 categories that can be associated with tasks in the plan. |
| id | String | The unique identifier for the plan details. It's 28 characters long and case-sensitive. [Format validation](https://learn.microsoft.com/en-us/graph/api/resources/planner-identifiers-disclaimer?view=graph-rest-1.0) is done on the service. Read-only. |
| sharedWith | [plannerUserIds](https://learn.microsoft.com/en-us/graph/api/resources/planneruserids?view=graph-rest-1.0) | Set of user IDs that this plan is shared with. If you're using Microsoft 365 groups, use the Groups API to manage group membership to share the [group's](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) plan. You can also add existing members of the group to this collection, although it isn't required for them to access the plan owned by the group. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "categoryDescriptions": {"@odata.type": "microsoft.graph.plannerCategoryDescriptions"},
  "id": "String (identifier)",
  "sharedWith": {"@odata.type": "microsoft.graph.plannerUserIds"}
}
```
