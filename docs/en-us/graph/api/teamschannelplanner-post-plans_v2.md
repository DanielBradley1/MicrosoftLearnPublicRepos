<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamschannelplanner-post-plans_v2?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# plan resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a plan in the Planner Unified plans Graph API. A plan belongs to a [container](https://learn.microsoft.com/en-us/graph/api/plancontainer?view=graph-rest-beta) and contains [buckets](https://learn.microsoft.com/en-us/graph/api/bucket?view=graph-rest-beta), [tasks](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta), and related planning data. Creation metadata is exposed through **creationInfo**, not top-level **createdBy** and **createdDateTime** properties.

Use the listed methods to create, read, update, and delete plans. The presence of a relationship doesn't imply that its related objects support standalone create, update, or delete operations. For supported nested creation, see [Create plan](https://learn.microsoft.com/en-us/graph/planner-post-plans_v2?view=graph-rest-beta).

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/planner-list-plans_v2?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) collection | Get a list of the plan objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/planner-post-plans_v2?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) | Create a new plan object. |
| [Get](https://learn.microsoft.com/en-us/graph/plan-get?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) | Read the properties and relationships of [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/plan-update?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) | Update the properties of a plan object. |
| [Delete](https://learn.microsoft.com/en-us/graph/planneruser-delete-v2?view=graph-rest-beta) | None | Delete a plan object. |
| [List buckets](https://learn.microsoft.com/en-us/graph/plan-list-buckets?view=graph-rest-beta) | [bucket](https://learn.microsoft.com/en-us/graph/api/bucket?view=graph-rest-beta) collection | Get a list of the bucket objects and their properties. |
| [Create bucket](https://learn.microsoft.com/en-us/graph/plan-post-buckets?view=graph-rest-beta) | [bucket](https://learn.microsoft.com/en-us/graph/api/bucket?view=graph-rest-beta) | Create a new bucket object. |
| [List contexts](https://learn.microsoft.com/en-us/graph/plan-list-contexts?view=graph-rest-beta) | [planContextLink](https://learn.microsoft.com/en-us/graph/api/plancontextlink?view=graph-rest-beta) collection | Get a list of the planContextLink objects and their properties. |
| [List customFieldDefinitions](https://learn.microsoft.com/en-us/graph/plan-list-customfielddefinitions?view=graph-rest-beta) | [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/customfielddefinition?view=graph-rest-beta) collection | Get a list of the customFieldDefinition objects and their properties. |
| [List dependencies](https://learn.microsoft.com/en-us/graph/plan-list-dependencies?view=graph-rest-beta) | [dependency](https://learn.microsoft.com/en-us/graph/api/dependency?view=graph-rest-beta) collection | Get a list of the dependency objects and their properties. |
| [List goals](https://learn.microsoft.com/en-us/graph/plan-list-goals?view=graph-rest-beta) | [goal](https://learn.microsoft.com/en-us/graph/api/goal?view=graph-rest-beta) collection | Get a list of the goal objects and their properties. |
| [List historyItems](https://learn.microsoft.com/en-us/graph/plan-list-historyitems?view=graph-rest-beta) | [historyItem](https://learn.microsoft.com/en-us/graph/api/historyitem?view=graph-rest-beta) collection | Get a list of the historyItem objects and their properties. |
| [List links](https://learn.microsoft.com/en-us/graph/plan-list-links?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/contentlink?view=graph-rest-beta) collection | Get a list of the contentLink objects and their properties. |
| [List tasks](https://learn.microsoft.com/en-us/graph/plan-list-tasks?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) collection | Get a list of the task objects and their properties. |
| [Create task](https://learn.microsoft.com/en-us/graph/planner-post-tasks_v2?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) | Create a task through the root task collection, with this plan's ID in the request body. |
| [Delete task](https://learn.microsoft.com/en-us/graph/plan-delete-tasks?view=graph-rest-beta) | None | Delete a task through its root task URL. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| archivalInfo | [plannerArchivalInfo](https://learn.microsoft.com/en-us/graph/api/plannerarchivalinfo?view=graph-rest-beta) | Service-populated information about whether the entity is archived, and when it was archived. Read-only. |
| calendar | [planCalendar](https://learn.microsoft.com/en-us/graph/api/plancalendar?view=graph-rest-beta) | Working-time calendar settings for the plan. |
| capabilities | [planCapability](https://learn.microsoft.com/en-us/graph/api/plancapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| container | [planContainer](https://learn.microsoft.com/en-us/graph/api/plancontainer?view=graph-rest-beta) | Identifies the group, Teams channel, or user that owns the plan. Required, and immutable after creation. |
| contentSensitivityLabelAssignment | [contentSensitivityLabelAssignment](https://learn.microsoft.com/en-us/graph/api/contentsensitivitylabelassignment?view=graph-rest-beta) | The sensitivity label assigned to content associated with the plan. |
| creationInfo | [creationInfo](https://learn.microsoft.com/en-us/graph/api/creationinfo?view=graph-rest-beta) | Read-only creation metadata for the entity. |
| displayName | String | Title of the plan. |
| duration | Int32 | Computed duration of the plan, in seconds. Read-only. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| hasChat | Boolean | Indicates whether the plan has an associated chat. Read-only. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/entity?view=graph-rest-beta) |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who last modified the entity. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the entity was last modified. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| planView | [planView](https://learn.microsoft.com/en-us/graph/api/planview?view=graph-rest-beta) | Plan-scoped view settings, including category definitions. |
| sharedWithContainers | [plannerSharedWithContainer](https://learn.microsoft.com/en-us/graph/api/plannersharedwithcontainer?view=graph-rest-beta) collection | The list of containers \(for example, additional groups or channels\) that the plan is shared with. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| buckets | [bucket](https://learn.microsoft.com/en-us/graph/api/bucket?view=graph-rest-beta) collection | The collection of buckets in the plan. Read-only. Nullable. |
| contexts | [planContextLink](https://learn.microsoft.com/en-us/graph/api/plancontextlink?view=graph-rest-beta) collection | Context links describing where the plan is surfaced. Can be supplied when creating a plan by using a deep insert. Nullable. |
| customFieldDefinitions | [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/customfielddefinition?view=graph-rest-beta) collection | The collection of custom field definitions in the plan. Read-only. Nullable. |
| dependencies | [dependency](https://learn.microsoft.com/en-us/graph/api/dependency?view=graph-rest-beta) collection | The collection of dependencies between items in the plan. Read-only. Nullable. |
| goals | [goal](https://learn.microsoft.com/en-us/graph/api/goal?view=graph-rest-beta) collection | The collection of goals in the plan. Read-only. Nullable. |
| historyItems | [historyItem](https://learn.microsoft.com/en-us/graph/api/historyitem?view=graph-rest-beta) collection | The collection of history \(audit\) items for the plan. Read-only. Nullable. |
| links | [contentLink](https://learn.microsoft.com/en-us/graph/api/contentlink?view=graph-rest-beta) collection | Content links attached to the plan. Can be supplied when creating a plan by using a deep insert. Nullable. |
| tasks | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) collection | The collection of tasks in the plan. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plan",
  "id": "String (identifier)",
  "displayName": "String",
  "container": {
    "@odata.type": "microsoft.graph.planContainer"
  },
  "calendar": {
    "@odata.type": "microsoft.graph.planCalendar"
  },
  "creationInfo": {
    "@odata.type": "microsoft.graph.creationInfo"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  },
  "planView": {
    "@odata.type": "microsoft.graph.planView"
  },
  "contentSensitivityLabelAssignment": {
    "@odata.type": "microsoft.graph.contentSensitivityLabelAssignment"
  },
  "hasChat": "Boolean",
  "duration": "Int32",
  "sharedWithContainers": [
    {
      "@odata.type": "microsoft.graph.plannerSharedWithContainer"
    }
  ],
  "capabilities": {
    "@odata.type": "microsoft.graph.planCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
