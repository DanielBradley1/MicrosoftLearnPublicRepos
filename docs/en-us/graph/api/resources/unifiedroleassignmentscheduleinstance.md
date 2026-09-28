<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentscheduleinstance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRoleAssignmentScheduleInstance resource type

Namespace: microsoft.graph

Represents the instance for an active role assignment in your tenant. The active assignment might have been made through [PIM assignments and activation requests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignmentschedulerequests?view=graph-rest-1.0), or directly through the [role assignments API](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0).

Inherits from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roleassignmentscheduleinstances?view=graph-rest-1.0) | [unifiedRoleAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentscheduleinstance?view=graph-rest-1.0) collection | Get the instances of active role assignments. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentscheduleinstance-get?view=graph-rest-1.0) | [unifiedRoleAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentscheduleinstance?view=graph-rest-1.0) | Get the instance of an active role assignment. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentscheduleinstance-filterbycurrentuser?view=graph-rest-1.0) | [unifiedRoleAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentscheduleinstance?view=graph-rest-1.0) collection | Get the instances of active role assignments for the calling principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appScopeId | String | Identifier of the app-specific scope when the assignment is scoped to an app. The scope of an assignment determines the set of resources for which the principal has been granted access. App scopes are scopes that are defined and understood by this application only. Use `/` for tenant-wide app scopes. Use **directoryScopeId** to limit the scope to particular directory objects, for example, administrative units. Supports `$filter` \(`eq`, `ne`, and on `null` values\). Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). |
| assignmentType | String | The type of the assignment that can either be `Assigned` or `Activated`. Supports `$filter` \(`eq`, `ne`\). |
| directoryScopeId | String | Identifier of the directory object representing the scope of the assignment. The scope of an assignment determines the set of resources for which the principal has been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. Use `/` for tenant-wide scope. Use **appScopeId** to limit the scope to an application only. Supports `$filter` \(`eq`, `ne`, and on `null` values\). Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). |
| endDateTime | DateTimeOffset | The end date of the schedule instance. |
| id | String | The unique identifier for the **unifiedRoleAssignmentScheduleInstance** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| memberType | String | How the assignment is inherited. It can either be `Inherited`, `Direct`, or `Group`. It can further imply whether the **unifiedRoleAssignmentSchedule** can be managed by the caller. Supports `$filter` \(`eq`, `ne`\). |
| principalId | String | Identifier of the principal that has been granted the role assignment. Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| roleAssignmentOriginId | String | The identifier of the role assignment in Microsoft Entra. Supports `$filter` \(`eq`, `ne`\). |
| roleAssignmentScheduleId | String | The identifier of the **unifiedRoleAssignmentSchedule** object from which this instance was created. Supports `$filter` \(`eq`, `ne`\). |
| roleDefinitionId | String | The identifier of the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object that is being assigned to the principal. Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| startDateTime | DateTimeOffset | When this instance starts. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activatedUsing | [unifiedRoleEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityscheduleinstance?view=graph-rest-1.0) | If the request is from an eligible administrator to activate a role, this parameter shows the related eligible assignment for that activation. Otherwise, it's `null`. Supports `$expand` and `$select` nested in `$expand`. |
| appScope | [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-1.0) | Read-only property with details of the app-specific scope when the assignment is scoped to an app. Nullable. Supports `$expand`. |
| directoryScope | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The directory object that is the scope of the assignment. Read-only. Supports `$expand`. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The principal that's getting a role assignment through the request. Supports `$expand` and `$select` nested in `$expand` for **id** only. |
| roleDefinition | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) | Detailed information for the roleDefinition object that is referenced through the **roleDefinitionId** property. Supports `$expand` and `$select` nested in `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleAssignmentScheduleInstance",
  "id": "String (identifier)",
  "principalId": "String",
  "roleDefinitionId": "String",
  "directoryScopeId": "String",
  "appScopeId": "String",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "assignmentType": "String",
  "memberType": "String",
  "roleAssignmentOriginId": "String",
  "roleAssignmentScheduleId": "String"
}
```
