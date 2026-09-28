<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# plannerRoster resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a collection of users who are collaborating on a [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta). A **plannerRoster** is a simple set of users, where everyone has the same level of permissions and they can be created by everyone, unless disabled by the tenant administrator. A **plannerRoster** can contain one plan.

Deleting a **plannerRoster** also deletes the plan and all tasks in the plan. A **plannerRoster** is also automatically deleted under the following conditions:

- The **plannerRoster** doesn't contain a plan 24 hours after its creation. Membership information is erased within 30 days of this deletion.
- The **plannerRoster** doesn't have any users remaining in the membership list because the last user removed themselves. Roster, its plan, and all contained tasks are deleted within 30 days of this operation.
- The **plannerRoster** doesn't have any users remaining in the membership list because the last user was permanently deleted. Roster, its plan, and all contained tasks are deleted immediately. Deleted users are permanently erased within 30 days of their deletion; however, tenant administrators can also choose to permanently delete users without this delay.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/planner-post-rosters?view=graph-rest-beta) | [plannerRoster](https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta) | Create a new [plannerRoster](https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/plannerroster-get?view=graph-rest-beta) | [plannerRoster](https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta) | Read the properties and relationships of a [plannerRoster](https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/plannerroster-delete?view=graph-rest-beta) | None | Delete a [plannerRoster](https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta) object. |
| [List members of roster](https://learn.microsoft.com/en-us/graph/api/plannerroster-list-members?view=graph-rest-beta) | [plannerRosterMember](https://learn.microsoft.com/en-us/graph/api/resources/plannerrostermember?view=graph-rest-beta) collection | Get the plannerRosterMember resources from the members navigation property. |
| [Add member to roster](https://learn.microsoft.com/en-us/graph/api/plannerroster-post-members?view=graph-rest-beta) | [plannerRosterMember](https://learn.microsoft.com/en-us/graph/api/resources/plannerrostermember?view=graph-rest-beta) | Create a new plannerRosterMember object. |
| [List plans in roster](https://learn.microsoft.com/en-us/graph/api/plannerroster-list-plans?view=graph-rest-beta) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) collection | Get the plannerPlan resources from the plans navigation property. |
| [List user's plans in rosters](https://learn.microsoft.com/en-us/graph/api/planneruser-list-rosterplans?view=graph-rest-beta) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) collection | Get the [plannerPlans](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) contained by the [plannerRosters](https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta) that the user is a member. |
| [Assign sensitivity label](https://learn.microsoft.com/en-us/graph/api/plannerroster-assignsensitivitylabel?view=graph-rest-beta) | [plannerRoster](https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta)\] | Assign a sensitivity label to a [plannerRoster](https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedSensitivityLabel | [sensitivityLabelAssignmentMethod](https://learn.microsoft.com/en-us/graph/api/resources/sensitivitylabelassignment?view=graph-rest-beta#sensitivitylabelassignmentmethod-values) | The sensitivity label applied to the roster. If mandatory labeling is enabled for the user and no label is specified, the user can't create the roster. Also, if labels are mandatory for the user, the user can't change the label of the roster to `null`. The possible values are: `standard`, `privileged`, `auto`, `unknownFutureValue`. |
| id | String | Identifier of the **plannerRoster**. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [plannerRosterMember](https://learn.microsoft.com/en-us/graph/api/resources/plannerrostermember?view=graph-rest-beta) collection | Retrieves the members of the **plannerRoster**. |
| plans | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) collection | Retrieves the plans contained by the **plannerRoster**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerRoster",
  "assignedSensitivityLabel": "#microsoft.graph.sensitivityLabelAssignment",
  "id": "String (identifier)"
}
```
