<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# plan resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A Planner V4 plan. A plan is discoverable through its owning [container](https://learn.microsoft.com/en-us/graph/api/resources/plancontainer?view=graph-rest-beta) \(a group, a Teams channel, or a user\), and contains [buckets](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta), [tasks](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta), [goals](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta), [dependencies](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta), and other Planner data. A plan is meaningless without its owning container, so `container` is returned by default along with `id`, `displayName`, `createdBy`, `createdDateTime`, `lastModifiedBy`, `lastModifiedDateTime`, and `archivalInfo/isArchived`.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/planneruser-list-v2?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) collection | Get a list of the plan objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/planneruser-post-v2?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) | Create a new plan object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/plan-get?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) | Read the properties and relationships of [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/plan-update?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) | Update the properties of a plan object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/planneruser-delete-v2?view=graph-rest-beta) | None | Delete a plan object. |
| [List buckets](https://learn.microsoft.com/en-us/graph/api/plan-list-buckets?view=graph-rest-beta) | [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta) collection | Get a list of the bucket objects and their properties. |
| [Create bucket](https://learn.microsoft.com/en-us/graph/api/plan-post-buckets?view=graph-rest-beta) | [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta) | Create a new bucket object. |
| [List contexts](https://learn.microsoft.com/en-us/graph/api/plan-list-contexts?view=graph-rest-beta) | [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta) collection | Get a list of the planContextLink objects and their properties. |
| [Create planContextLink](https://learn.microsoft.com/en-us/graph/api/plan-post-contexts?view=graph-rest-beta) | [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta) | Create a new planContextLink object. |
| [List customFieldDefinitions](https://learn.microsoft.com/en-us/graph/api/plan-list-customfielddefinitions?view=graph-rest-beta) | [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) collection | Get a list of the customFieldDefinition objects and their properties. |
| [Add customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/plan-post-customfielddefinitions?view=graph-rest-beta) | [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) | Add customFieldDefinitions by posting to the customFieldDefinitions collection. |
| [Remove customFieldDefinitions](https://learn.microsoft.com/en-us/graph/api/plan-delete-customfielddefinitions?view=graph-rest-beta) | None | Remove a [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) object. |
| [List dependencies](https://learn.microsoft.com/en-us/graph/api/plan-list-dependencies?view=graph-rest-beta) | [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta) collection | Get a list of the dependency objects and their properties. |
| [Add dependency](https://learn.microsoft.com/en-us/graph/api/plan-post-dependencies?view=graph-rest-beta) | [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta) | Add dependencies by posting to the dependencies collection. |
| [Remove dependencies](https://learn.microsoft.com/en-us/graph/api/plan-delete-dependencies?view=graph-rest-beta) | None | Remove a [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta) object. |
| [List goals](https://learn.microsoft.com/en-us/graph/api/plan-list-goals?view=graph-rest-beta) | [goal](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta) collection | Get a list of the goal objects and their properties. |
| [Add goal](https://learn.microsoft.com/en-us/graph/api/plan-post-goals?view=graph-rest-beta) | [goal](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta) | Add goals by posting to the goals collection. |
| [Remove goals](https://learn.microsoft.com/en-us/graph/api/plan-delete-goals?view=graph-rest-beta) | None | Remove a [goal](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta) object. |
| [List historyItems](https://learn.microsoft.com/en-us/graph/api/plan-list-historyitems?view=graph-rest-beta) | [historyItem](https://learn.microsoft.com/en-us/graph/api/resources/historyitem?view=graph-rest-beta) collection | Get a list of the historyItem objects and their properties. |
| [Add historyItem](https://learn.microsoft.com/en-us/graph/api/plan-post-historyitems?view=graph-rest-beta) | [historyItem](https://learn.microsoft.com/en-us/graph/api/resources/historyitem?view=graph-rest-beta) | Add historyItems by posting to the historyItems collection. |
| [Remove historyItems](https://learn.microsoft.com/en-us/graph/api/plan-delete-historyitems?view=graph-rest-beta) | None | Remove a [historyItem](https://learn.microsoft.com/en-us/graph/api/resources/historyitem?view=graph-rest-beta) object. |
| [List links](https://learn.microsoft.com/en-us/graph/api/plan-list-links?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) collection | Get a list of the contentLink objects and their properties. |
| [Create contentLink](https://learn.microsoft.com/en-us/graph/api/plan-post-links?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) | Create a new contentLink object. |
| [List tasks](https://learn.microsoft.com/en-us/graph/api/plan-list-tasks?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) collection | Get a list of the task objects and their properties. |
| [Add task](https://learn.microsoft.com/en-us/graph/api/plan-post-tasks?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) | Add tasks by posting to the tasks collection. |
| [Remove tasks](https://learn.microsoft.com/en-us/graph/api/plan-delete-tasks?view=graph-rest-beta) | None | Remove a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| archivalInfo | [plannerArchivalInfo](https://learn.microsoft.com/en-us/graph/api/resources/plannerarchivalinfo?view=graph-rest-beta) | Information about whether the entity is archived, and when it was archived. |
| calendar | [planCalendar](https://learn.microsoft.com/en-us/graph/api/resources/plancalendar?view=graph-rest-beta) | Working-time calendar settings for the plan. |
| capabilities | [planCapability](https://learn.microsoft.com/en-us/graph/api/resources/plancapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| container | [planContainer](https://learn.microsoft.com/en-us/graph/api/resources/plancontainer?view=graph-rest-beta) | Identifies the group, Teams channel, or user that owns the plan. Required, and immutable after creation. |
| contentSensitivityLabelAssignment | [contentSensitivityLabelAssignment](https://learn.microsoft.com/en-us/graph/api/resources/contentsensitivitylabelassignment?view=graph-rest-beta) | The sensitivity label assigned to content associated with the plan. |
| creationInfo | [creationInfo](https://learn.microsoft.com/en-us/graph/api/resources/creationinfo?view=graph-rest-beta) | Read-only creation metadata for the entity. |
| displayName | String | Title of the plan. |
| duration | Int32 | Duration of the plan, in days. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| hasChat | Boolean | Indicates whether the plan has an associated chat. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who last modified the entity. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the entity was last modified. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| planView | [planView](https://learn.microsoft.com/en-us/graph/api/resources/planview?view=graph-rest-beta) | Plan-scoped view settings, including category definitions. |
| sharedWithContainers | [plannerSharedWithContainer](https://learn.microsoft.com/en-us/graph/api/resources/plannersharedwithcontainer?view=graph-rest-beta) collection | The list of containers \(for example, additional groups or channels\) that the plan is shared with. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| buckets | [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta) collection | The collection of buckets in the plan. Read-only. Nullable. |
| contexts | [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta) collection | The collection of context links describing where the plan is surfaced. Read-only. Nullable. |
| customFieldDefinitions | [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) collection | The collection of custom field definitions in the plan. Read-only. Nullable. |
| dependencies | [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta) collection | The collection of dependencies between items in the plan. Read-only. Nullable. |
| goals | [goal](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta) collection | The collection of goals in the plan. Read-only. Nullable. |
| historyItems | [historyItem](https://learn.microsoft.com/en-us/graph/api/resources/historyitem?view=graph-rest-beta) collection | The collection of history \(audit\) items for the plan. Read-only. Nullable. |
| links | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) collection | The collection of content links attached to the plan. Read-only. Nullable. |
| tasks | [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) collection | The collection of tasks in the plan. Read-only. Nullable. |

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
