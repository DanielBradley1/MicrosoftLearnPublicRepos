<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# businessScenarioTask resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta) that is associated with a [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) and contains additional scenario data.

Inherits from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/businessscenarioplanner-list-tasks?view=graph-rest-beta) | [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) collection | Get a list of the [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/businessscenarioplanner-post-tasks?view=graph-rest-beta) | [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) | Create a new [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/businessscenariotask-get?view=graph-rest-beta) | [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) | Read the properties and relationships of a [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/businessscenariotask-update?view=graph-rest-beta) | [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) | Update the properties of a [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/businessscenarioplanner-delete-tasks?view=graph-rest-beta) | None | Delete a [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeChecklistItemCount | Int32 | Number of checklist items with value set to `false`, representing incomplete items. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| appliedCategories | [plannerAppliedCategories](https://learn.microsoft.com/en-us/graph/api/resources/plannerappliedcategories?view=graph-rest-beta) | The categories to which the task has been applied. For possible values, see [plannerAppliedCategories](https://learn.microsoft.com/en-us/graph/api/resources/plannerappliedcategories?view=graph-rest-beta). Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| assigneePriority | String | Hint used to order items of this type in a list view. For details about the supported format, see [Using order hints in Planner](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-beta). Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| assignments | [plannerAssignments](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignments?view=graph-rest-beta) | The set of assignees the task is assigned to. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| bucketId | String | Bucket ID to which the task belongs. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| businessScenarioProperties | [businessScenarioProperties](https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioproperties?view=graph-rest-beta) | Scenario-specific properties of the task. **externalObjectId** and **externalBucketId** properties must be specified when creating a task. |
| checklistItemCount | Int32 | Number of checklist items that are present on the task. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| completedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who completed the task. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). Read-Only. |
| completedDateTime | DateTimeOffset | Date and time at which the **percentComplete** of the task is set to `100`. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). Read-only. |
| conversationThreadId | String | Thread ID of the conversation on the task. This property contains the ID of the conversation thread object created in the **group**. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who created the task. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). Read-Only. |
| createdDateTime | DateTimeOffset | Date and time at which the task is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). Read-only. |
| creationSource | [plannerTaskCreation](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskcreation?view=graph-rest-beta) | Contains information about the origin of the task. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| dueDateTime | DateTimeOffset | Date and time at which the task is due. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| hasDescription | Boolean | `True` indicates that the details object of the task has a nonempty description; otherwise, `false`. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). Read-only. |
| id | String | The unique identifier for the task. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Read-only. |
| orderHint | String | Hint used to order items of this type in a list view. For details about the supported format, see [Using order hints in Planner](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-beta). Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| percentComplete | Int32 | Percentage of task completion. When set to `100`, the task is considered completed. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| planId | String | Identifier of the plan to which the task belongs. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| previewType | plannerPreviewType | This sets the type of preview that shows up on the task. The possible values are: `automatic`, `noPreview`, `checklist`, `description`, `reference`. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| priority | Int32 | Priority of the task. Valid range of values is between `0` and `10` \(inclusive\), with increasing value being lower priority \(`0` has the highest priority and `10` has the lowest priority\). Currently, Planner interprets values `0` and `1` as "urgent", `2`, `3`, and `4` as "important", `5`, `6`, and `7` as "medium", and `8`, `9`, and `10` as "low". Currently, Planner sets the value `1` for "urgent", `3` for "important", `5` for "medium", and `9` for "low". Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| referenceCount | Int32 | Number of external references that exist on the task. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| startDateTime | DateTimeOffset | Date and time at which the task starts. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| target | [businessScenarioTaskTargetBase](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotasktargetbase?view=graph-rest-beta) | Target of the task that specifies where the task should be placed. Must be specified when creating a task. |
| title | String | Title of the task. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignedToTaskBoardFormat | [plannerAssignedToTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignedtotaskboardtaskformat?view=graph-rest-beta) | Used to render the task correctly in the task board view when grouped by **assignedTo**. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| bucketTaskBoardFormat | [plannerBucketTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerbuckettaskboardtaskformat?view=graph-rest-beta) | Used to render the task correctly in the task board view when grouped by **bucket**. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| details | [plannerTaskDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-beta) | Additional details about the task. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| progressTaskBoardFormat | [plannerProgressTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerprogresstaskboardtaskformat?view=graph-rest-beta) | Used to render the task correctly in the task board view when grouped by **progress**. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.businessScenarioTask",
  "activeChecklistItemCount": "Int32",
  "appliedCategories": {"@odata.type": "microsoft.graph.plannerAppliedCategories"},
  "assigneePriority": "String",
  "assignments": {"@odata.type": "microsoft.graph.plannerAssignments"},
  "bucketId": "String",
  "businessScenarioProperties": {"@odata.type": "microsoft.graph.businessScenarioProperties"},
  "checklistItemCount": "Int32",
  "completedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "completedDateTime": "String (timestamp)",
  "conversationThreadId": "String",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "creationSource": {"@odata.type": "microsoft.graph.plannerTaskCreation"},
  "dueDateTime": "String (timestamp)",
  "hasDescription": "Boolean",
  "id": "String (identifier)",
  "orderHint": "String",
  "percentComplete": "Int32",
  "planId": "String",
  "previewType": "String",
  "priority": "Int32",
  "referenceCount": "Int32",
  "startDateTime": "String (timestamp)",
  "target": {"@odata.type": "microsoft.graph.businessScenarioTaskTargetBase"},
  "title": "String"
}
```
