<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRoleEligibilitySchedule resource type

Namespace: microsoft.graph

Represents a schedule for a role eligibility in your tenant and is used to instantiate a [unifiedRoleEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityscheduleinstance?view=graph-rest-1.0).

Inherits from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roleeligibilityschedules?view=graph-rest-1.0) | [unifiedRoleEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedule?view=graph-rest-1.0) collection | Get the schedules for role eligibility operations. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedroleeligibilityschedule-get?view=graph-rest-1.0) | [unifiedRoleEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedule?view=graph-rest-1.0) | Retrieve the schedule for a role eligibility operation. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/unifiedroleeligibilityschedule-filterbycurrentuser?view=graph-rest-1.0) | [unifiedRoleEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedule?view=graph-rest-1.0) collection | Retrieve the schedules for role eligibilities for which the signed-in user is the principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appScopeId | String | Identifier of the app-specific scope when the role eligibility is scoped to an app. The scope of a role eligibility determines the set of resources for which the principal has been granted access. App scopes are scopes that are defined and understood by this application only. Use `/` for tenant-wide app scopes. Use **directoryScopeId** to limit the scope to particular directory objects, for example, administrative units. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| createdDateTime | DateTimeOffset | When the schedule was created. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). |
| createdUsing | String | Identifier of the object through which this schedule was created. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| directoryScopeId | String | Identifier of the directory object representing the scope of the role eligibility. The scope of a role eligibility determines the set of resources for which the principal has been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. Use `/` for tenant-wide scope. Use **appScopeId** to limit the scope to an application only. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| id | String | The unique identifier for the schedule object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Supports `$filter` \(`eq`\). |
| memberType | String | How the role eligibility is inherited. It can either be `Inherited`, `Direct`, or `Group`. It can further imply whether the **unifiedRoleEligibilitySchedule** can be managed by the caller. Supports `$filter` \(`eq`, `ne`\). |
| modifiedDateTime | DateTimeOffset | When the schedule was last modified. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). |
| principalId | String | Identifier of the principal that is eligible for a role.Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| roleDefinitionId | String | Identifier of the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object that a principal is eligible for. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | The period of the role eligibility. |
| status | String | The status of the role eligibility request. Inherited from [unifiedRoleScheduleBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0). The possible values are: `Canceled`, `Denied`, `Failed`, `Granted`, `PendingAdminDecision`, `PendingApproval`, `PendingProvisioning`, `PendingScheduleCreation`, `Provisioned`, `Revoked`, and `ScheduleCreated`. Not nullable. Supports `$filter` \(`eq`, `ne`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appScope | [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-1.0) | Read-only property with details of the app-specific scope when the role eligibility is scoped to an app. Nullable. Supports `$expand`. |
| directoryScope | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The directory object that is the scope of the role eligibility. Read-only. Supports `$expand`. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The principal that's eligible for a role through the request. Supports `$expand`. |
| roleDefinition | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) | Detailed information for the roleDefinition object that is referenced through the **roleDefinitionId** property. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleEligibilitySchedule",
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
  "memberType": "String"
}
```
