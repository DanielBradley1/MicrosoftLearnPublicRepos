<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# plannerDelta resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents the base type for planner entities such as a plan or a task.

Base type of [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-beta), [plannerGoal](https://learn.microsoft.com/en-us/graph/api/resources/plannergoal?view=graph-rest-beta), [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta), [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta), and [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta).

Derived types in the Planner Unified plans Graph API include [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta), [categoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/categorydefinition?view=graph-rest-beta), [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta), [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta), [customChoiceOption](https://learn.microsoft.com/en-us/graph/api/resources/customchoiceoption?view=graph-rest-beta), [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta), [customFieldValue](https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta), [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta), [goal](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta), [historyItem](https://learn.microsoft.com/en-us/graph/api/resources/historyitem?view=graph-rest-beta), [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta), [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta), [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta), [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta), and [userAssignment](https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta). Each resource's Methods section identifies its documented operations; inheritance doesn't imply CRUD support.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerDelta",
  "id": "String (identifier)"
}
```
