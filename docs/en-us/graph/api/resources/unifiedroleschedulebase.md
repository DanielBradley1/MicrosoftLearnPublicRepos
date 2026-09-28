<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleschedulebase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# unifiedRoleScheduleBase resource type

Namespace: microsoft.graph

A template that exposes properties and relationships used in [unifiedRoleAssignmentSchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedule?view=graph-rest-1.0) and [unifiedRoleEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedule?view=graph-rest-1.0) resource types.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appScopeId | String | Identifier of the app-specific scope when the assignment or eligibility is scoped to an app. The scope of an assignment or eligibility determines the set of resources for which the principal has been granted access. App scopes are scopes that are defined and understood by this application only. Use `/` for tenant-wide app scopes. Use **directoryScopeId** to limit the scope to particular directory objects, for example, administrative units. |
| createdDateTime | DateTimeOffset | When the schedule was created. |
| createdUsing | String | Identifier of the object through which this schedule was created. |
| directoryScopeId | String | Identifier of the directory object representing the scope of the assignment or eligibility. The scope of an assignment or eligibility determines the set of resources for which the principal has been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. Use `/` for tenant-wide scope. Use **appScopeId** to limit the scope to an application only. |
| id | String | The unique identifier for the schedule object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| modifiedDateTime | DateTimeOffset | When the schedule was last modified. |
| principalId | String | Identifier of the principal that has been granted the role assignment or eligibility. |
| roleDefinitionId | String | Identifier of the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object that is being assigned to the principal or that a principal is eligible for. |
| status | String | The status of the role assignment or eligibility request. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appScope | [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-1.0) | Read-only property with details of the app-specific scope when the role eligibility or assignment is scoped to an app. Nullable. |
| directoryScope | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The directory object that is the scope of the role eligibility or assignment. Read-only. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The principal that's getting a role assignment or that's eligible for a role through the request. |
| roleDefinition | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) | Detailed information for the roleDefinition object that is referenced through the **roleDefinitionId** property. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleScheduleBase",
  "id": "String (identifier)",
  "principalId": "String",
  "roleDefinitionId": "String",
  "directoryScopeId": "String",
  "appScopeId": "String",
  "createdUsing": "String",
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "status": "String"
}
```
