<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/planner-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# Use the Planner REST API

You can use the Planner API in Microsoft Graph to create tasks and assign them to users in a group in Microsoft 365.

Before you get started with the Planner API, it will be helpful to understand how the main objects relate to each other as well as to Microsoft 365 groups.

## Plan containers

In Microsoft Planner, plans are always contained by another resource. The containing resource determines the authorization rules of the plan and all the tasks in it, as well as the lifecycle of the plan. For example, for plans contained by Microsoft 365 groups, group members will be able to create, edit, resolve, and delete tasks in the plan, as well as changing some plan-level properties, such as the name of the plan or label names. Additionally, when the group is deleted, all the plans in the group are automatically deleted, or if a group is restored, all the plans will be automatically restored.

The most common type of container is a Microsoft 365 group.

Important

Premium plans and tasks aren't available on the Planner API in Microsoft Graph. Only basic plans may be accessed using this API.

### Container type: Microsoft 365 groups

Plans are commonly contained in Microsoft 365 groups in the Planner API. To [get the plans owned by a group](https://learn.microsoft.com/en-us/graph/api/plannergroup-list-plans?view=graph-rest-1.0), make the following HTTP request.

```http
GET /groups/{group-id}/planner/plans
```

When you [create a new plan](https://learn.microsoft.com/en-us/graph/api/planner-post-plans?view=graph-rest-1.0), set the **container** property on a plan object to make a group its container. Plans must be contained by a supported resource.

> **Note:** The user who is creating the plan must be a member of the group that will contain the plan. When you create a new group by using [Create group](https://learn.microsoft.com/en-us/graph/api/group-post-groups?view=graph-rest-1.0), you are not added to the group as a member. After the group is created, add yourself as a member by using [group post members](https://learn.microsoft.com/en-us/graph/api/group-post-members?view=graph-rest-1.0).

## Plans

[Plans](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) are the containers of [tasks](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0). To [create a task in a plan](https://learn.microsoft.com/en-us/graph/api/planner-post-tasks?view=graph-rest-1.0), set the **planId** property on the task object to the ID of the plan while creating the task. Tasks currently cannot be created without plans. To [retrieve the tasks in a plan](https://learn.microsoft.com/en-us/graph/api/plannerplan-list-tasks?view=graph-rest-1.0), make the following HTTP request.

```http
GET /planner/plans/{plan-id}/tasks
```

## Tasks

Each task can be assigned to a user by adding an [assignment](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignment?view=graph-rest-1.0) in the [assignments](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignments?view=graph-rest-1.0) property on the task object. The ID of the user to assign the task is the name of the open property on **assignments**, and the **orderHint** property on the assignment must be specified.

## Task and plan details

Planner resources are arranged into basic objects and detail objects. Basic objects provide access to common properties of the resources, suitable for list views, while the detail objects provide access to large properties of the resources suitable for drill down views.

## Visualization

Aside from task and plan data, the Planner API also provides resources for creating a common visualization of data across clients. Several types of visualization data are available for tasks, as listed in the following table.

| Tasks are shown as | Tasks are ordered with information from |
| :--- | :--- |
| Flat list \(tasks in a plan\) | **orderHint** property on tasks |
| Flat list \(tasks assigned to a user\) | **assigneePriority** property on tasks |
| Board view with columns for assignees \(assigned to task board\) | [assignedToTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignedtotaskboardtaskformat?view=graph-rest-1.0) object |
| Board view with columns for progress of the task towards completion \(progress task board\) | [progressTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerprogresstaskboardtaskformat?view=graph-rest-1.0) object |
| Board view with custom columns of tasks \(bucket task board\): | [bucketTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerbuckettaskboardtaskformat?view=graph-rest-1.0) object |

The custom columns in the bucket task board are represented by [bucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0) objects, and their order by **orderHint** property on the object.

All the ordering is controlled by the principles described in [Planner order hints](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0).

## Planner resource versioning

Planner versions all resources using etags. These etags are returned with **@odata.etag** property on each resource. `PATCH` and `DELETE` requests require the last etag known by the client to be specified with a `If-Match` header. Planner allows changes to older versions of resources, if the intended change does not conflict with newer changes accepted by the Planner service on the same resource. The clients can identify which etag for the same resource is newer by calculating which etag value is greater in ordinal string comparison. Each resource has a unique etag. Etag values for different resources, including those with containment relationships, cannot be compared. The client apps are expected to handle versioning related [error codes](https://learn.microsoft.com/en-us/graph/errors) `409` and `412` by reading the latest version of the item and resolving the conflicting changes.

## Common Planner error conditions

In addition to [general errors](https://learn.microsoft.com/en-us/graph/errors) that apply to Microsoft Graph, some error conditions are specific to the Planner API.

### 400 Bad request

In some common scenarios, `POST` and `PATCH` requests can return a 400 status code. The following are some of the common causes:

- Open Type properties are not of correct types, or the type isn't specified, or they do not contain any properties. For example, [plannerAssignments](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignments?view=graph-rest-1.0) properties with complex values need to declare **@odata.type** property with value `microsoft.graph.plannerAssignment`.
- Order hint values do not have the [correct format](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). For example, an order hint value is being set directly to the value returned to the client.
- The data is logically inconsistent. For example, start date of task is later than due date of the task.

### 403 Forbidden

In addition to the general errors, the Planner API also returns the `403` status code when a service-defined limit has been exceeded. If this is the case, the **code** property on the error resource type will indicate the type of the limit exceeded by the request. For details about the limits, see [Planner limits](https://learn.microsoft.com/en-us/office365/planner/planner-limits) . The following are the possible values for the limit types.

| Value | Description |
| :--- | :--- |
| MaximumProjectsOwnedByUser | The maximum number of plans contained by a group limit has been exceeded. This limit applies to plans contained by a group based on the **container** property of the [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) resource. |
| MaximumProjectsSharedWithUser | The maximum number of plans shared with a user limit has been exceeded. This limit is based on the **sharedWith** property on the [plannerPlanDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannerplandetails?view=graph-rest-1.0) resource. |
| MaximumTasksCreatedByUser | The maximum number of tasks created by a user limit has been exceeded. This limit is based on the **createdBy** property on the [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) resource. |
| MaximumTasksAssignedToUser | The maximum number of tasks assigned to a user limit has been exceeded. This limit is based on the **assignments** property on the [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) resource. |
| MaximumTasksInProject | The maximum number of tasks in a plan limit has been exceeded. This limit is based on the **planId** property on the [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) resource. |
| MaximumActiveTasksInProject | The maximum number of tasks that aren't completed in a plan limit has been exceeded. This limit is based on the **planId** and **percentComplete** properties on the [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) resource. |
| MaximumBucketsInProject | The maximum number of buckets in a plan limit has been exceeded. This limit is based on the **planId** property on the [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0) resource. |
| MaximumUsersSharedWithProject | The **sharedWith** property on the [plannerPlanDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannerplandetails?view=graph-rest-1.0) resource contains too many values. |
| MaximumReferencesOnTask | The **references** property on the [plannerTaskDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-1.0) resource contains too many values. |
| MaximumChecklistItemsOnTask | The **checklist** property on the [plannerTaskDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-1.0) resource contains too many values. |
| MaximumAssigneesInTasks | The **assignments** property on the [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) resource contains too many values. |
| MaximumPlannerPlans | The **group** already contains the maximum number of **plans** owned by a user, which is currently 200. For details about limits, see [Planner limits](https://learn.microsoft.com/en-us/office365/planner/planner-limits). |

### 412 Precondition Failed

All Planner API `POST`, `PATCH`, and `DELETE` requests require the `If-Match` header to be specified with the last known etag value of the resource that is subject to the request. The 412 status code can also be returned if the etag value specified in the request no longer matches a version of the resource in the service. In this case, the clients should read the resource again and get a new etag.
