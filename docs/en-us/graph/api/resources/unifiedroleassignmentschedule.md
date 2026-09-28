<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-12 -->

# unifiedRoleAssignmentSchedule resource type

Namespace: microsoft.graph

Represents a schedule for an active role assignment in your tenant and is used to instantiate a [unifiedRoleAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentscheduleinstance?view=graph-rest-1.0). The active assignment might have been made through [PIM assignments and activation requests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignmentschedulerequests?view=graph-rest-1.0), or directly through the [role assignments API](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0).

Inherits from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roleassignmentschedules?view=graph-rest-1.0) | [unifiedRoleAssignmentSchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedule?view=graph-rest-1.0) collection | Get the schedules for active role assignment operations. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentschedule-get?view=graph-rest-1.0) | [unifiedRoleAssignmentSchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedule?view=graph-rest-1.0) | Retrieve the schedule for an active role assignment operation. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentschedule-filterbycurrentuser?view=graph-rest-1.0) | [unifiedRoleAssignmentSchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedule?view=graph-rest-1.0) collection | Retrieve the schedules for active role assignment operations for which the signed-in user is the principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appScopeId | String | Identifier of the app-specific scope when the assignment is scoped to an app. The scope of an assignment determines the set of resources for which the principal has been granted access. App scopes are scopes that are defined and understood by this application only. Use `/` for tenant-wide app scopes. Use **directoryScopeId** to limit the scope to particular directory objects, for example, administrative units. Supports `$filter` \(`eq`, `ne`, and on `null` values\). Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). |
| assignmentType | String | The type of the assignment that can either be `Assigned` or `Activated`. Supports `$filter` \(`eq`, `ne`\). |
| createdDateTime | DateTimeOffset | When the schedule was created. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). |
| createdUsing | String | Identifier of the **unifiedRoleAssignmentScheduleRequest** object through which this schedule was created. Nullable. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| directoryScopeId | String | Identifier of the directory object representing the scope of the assignment. The scope of an assignment determines the set of resources for which the principal has been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. Use `/` for tenant-wide scope. Use **appScopeId** to limit the scope to an application only. Supports `$filter` \(`eq`, `ne`, and on `null` values\). Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). |
| id | String | The unique identifier for the **unifiedRoleAssignmentScheduleRequest** object. Supports `$filter` \(`eq`\). Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| memberType | String | How the assignment is inherited. It can either be `Inherited`, `Direct`, or `Group`. It can further imply whether the **unifiedRoleAssignmentSchedule** can be managed by the caller. Supports `$filter` \(`eq`, `ne`\). |
| modifiedDateTime | DateTimeOffset | When the schedule was last modified. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). |
| principalId | String | Identifier of the principal that has been granted the role assignment. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| roleDefinitionId | String | Identifier of the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object that is being assigned to the principal. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | The period of the role assignment. It can represent a single occurrence or multiple recurrences. |
| status | String | The status of the **unifiedRoleAssignmentScheduleRequest** object. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). The possible values are: `Canceled`, `Denied`, `Failed`, `Granted`, `PendingAdminDecision`, `PendingApproval`, `PendingProvisioning`, `PendingScheduleCreation`, `Provisioned`, `Revoked`, and `ScheduleCreated`. Not nullable. Supports `$filter` \(`eq`, `ne`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activatedUsing | [unifiedRoleEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedule?view=graph-rest-1.0) | If the request is from an eligible administrator to activate a role, this parameter shows the related eligible assignment for that activation. Otherwise, it's `null`. Supports `$expand`. |
| appScope | [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-1.0) | Read-only property with details of the app-specific scope when the assignment is scoped to an app. Nullable. Supports `$expand`. |
| directoryScope | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The directory object that is the scope of the assignment. Read-only. Supports `$expand`. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The principal that's getting a role assignment through the request. Supports `$expand` and `$select` nested in `$expand` for **id** only. |
| roleDefinition | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) | Detailed information for the roleDefinition object that is referenced through the **roleDefinitionId** property. Supports `$expand` and `$select` nested in `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleAssignmentSchedule",
  "id": "String (identifier)",
  "principalId": "String",
  "roleDefinitionId": "String",
  "directoryScopeId": "String",
  "appScopeId": "String",
  "createdUsing": "String",
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "status": "String",
  "scheduleInfo": {
    "@odata.type": "microsoft.graph.requestSchedule"
  },
  "assignmentType": "String",
  "memberType": "String"
}
```
