<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# task resource type \(case management\)

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a unit of work that must be completed as part of a [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta).

This resource inherits from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-list-tasks?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.task](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta) collection | Get a list of tasks for a case. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-post-tasks?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.task](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta) | Create a task for a case. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-task-get?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.task](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta) | Read the properties and relationships of [microsoft.graph.security.caseManagement.task](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-task-update?view=graph-rest-beta) | None | Update all client-managed properties of a task. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-task-delete?view=graph-rest-beta) | None | Delete a task from a case. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | String | The user assigned to the task. Supports `$filter`. |
| category | [microsoft.graph.security.caseManagement.caseTaskCategory](#casetaskcategory-values) | The functional category of the task. Supports `$filter`. |
| closingNotes | String | Notes recorded when the task is completed. Supports `$filter`. |
| createdBy | String | The user or service that created the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| createdDateTime | DateTimeOffset | The date and time when the resource was created. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| description | String | The description of the task. Supports `$filter`. |
| displayName | String | The title of the task. Supports `$filter`. |
| dueDateTime | DateTimeOffset | The target completion date and time for the task. Supports `$filter`. |
| id | String | The unique identifier for the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter`. |
| lastModifiedBy | String | The user or service that last modified the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| priority | [microsoft.graph.security.caseManagement.caseTaskPriority](#casetaskpriority-values) | The priority assigned to the task. Supports `$filter`. |
| status | [microsoft.graph.security.caseManagement.taskStatus](#taskstatus-values) | The lifecycle state of the task. Supports `$filter`. |

### caseTaskCategory values

| Member | Description |
| :--- | :--- |
| uncategorized | Uncategorized task. |
| triage | Task for triaging the case. |
| contain | Task for containing the threat. |
| investigate | Task for investigating the case. |
| remediate | Task for remediating the issue. |
| prevent | Task for preventing recurrence. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### caseTaskPriority values

| Member | Description |
| :--- | :--- |
| notSet | No priority is set. |
| veryLow | Very low priority task. |
| low | Low priority task. |
| medium | Medium priority task. |
| high | High priority task. |
| critical | Critical priority task. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### taskStatus values

| Member | Description |
| :--- | :--- |
| notSet | No status is set. |
| new | New task. |
| inProgress | Task is in progress. |
| failed | Task failed. |
| partiallyCompleted | Task is partially completed. |
| skipped | Task was skipped. |
| completed | Task is completed. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.task",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "displayName": "String",
  "status": "String",
  "description": "String",
  "assignedTo": "String",
  "closingNotes": "String",
  "dueDateTime": "String (timestamp)",
  "priority": "String",
  "category": "String"
}
```
