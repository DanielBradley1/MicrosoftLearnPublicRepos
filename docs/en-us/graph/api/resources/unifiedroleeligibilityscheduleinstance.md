<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityscheduleinstance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRoleEligibilityScheduleInstance resource type

Namespace: microsoft.graph

Represents the instance for a role eligibility in your tenant.

Inherits from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roleeligibilityscheduleinstances?view=graph-rest-1.0) | [unifiedRoleEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityscheduleinstance?view=graph-rest-1.0) collection | Get the instances of role eligibilities. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedroleeligibilityscheduleinstance-get?view=graph-rest-1.0) | [unifiedRoleEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityscheduleinstance?view=graph-rest-1.0) | Get the instance of a role eligibility. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/unifiedroleeligibilityscheduleinstance-filterbycurrentuser?view=graph-rest-1.0) | [unifiedRoleEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityscheduleinstance?view=graph-rest-1.0) collection | Get the instances of eligible roles for the calling principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appScopeId | String | Identifier of the app-specific scope when the role eligibility is scoped to an app. The scope of the role eligibility determines the set of resources for which the principal has been granted access. App scopes are scopes that are defined and understood by this application only. Use `/` for tenant-wide app scopes. Use **directoryScopeId** to limit the scope to particular directory objects, for example, administrative units. Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| directoryScopeId | String | Identifier of the directory object representing the scope of the role eligibility. The scope of the role eligibility determines the set of resources for which the principal has been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. Use `/` for tenant-wide scope. Use **appScopeId** to limit the scope to an application only. Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| endDateTime | DateTimeOffset | The end date of the schedule instance. |
| id | String | The unique identifier for the schedule object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| memberType | String | How the role eligibility is inherited. It can either be `Inherited`, `Direct`, or `Group`. It can further imply whether the **unifiedRoleEligibilitySchedule** can be managed by the caller. Supports `$filter` \(`eq`, `ne`\). |
| principalId | String | Identifier of the principal that's eligible for a role. Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| roleDefinitionId | String | Identifier of the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object that the principal is eligible for. Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| roleEligibilityScheduleId | String | The identifier of the **unifiedRoleEligibilitySchedule** object from which this instance was created. Supports `$filter` \(`eq`, `ne`\). |
| startDateTime | DateTimeOffset | When this instance starts. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appScope | [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-1.0) | Read-only property with details of the app-specific scope when the role eligibility is scoped to an app. Nullable. Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). Supports `$expand`. |
| directoryScope | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The directory object that is the scope of the role eligibility. Read-only. Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). Supports `$expand`. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The principal that's getting a role eligibility through the request. Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). Supports `$expand`. |
| roleDefinition | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) | Detailed information for the roleDefinition object that is referenced through the **roleDefinitionId** property. Inherited from [unifiedRoleScheduleInstanceBase](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolescheduleinstancebase?view=graph-rest-1.0). Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleEligibilityScheduleInstance",
  "id": "String (identifier)",
  "principalId": "String",
  "roleDefinitionId": "String",
  "directoryScopeId": "String",
  "appScopeId": "String",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "memberType": "String",
  "roleEligibilityScheduleId": "String"
}
```
