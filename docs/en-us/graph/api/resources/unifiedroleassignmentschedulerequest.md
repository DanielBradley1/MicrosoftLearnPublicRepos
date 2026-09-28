<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRoleAssignmentScheduleRequest resource type

Namespace: microsoft.graph

In PIM, represents a request for an active role assignment to a principal. The role assignment can be permanently active with or without an expiry date, or temporarily active after activation of an eligible assignment. Inherits from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0).

For more information about PIM scenarios you can define through the **unifiedRoleAssignmentScheduleRequest** resource type, see [Overview of role management through the privileged identity management \(PIM\) API](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roleassignmentschedulerequests?view=graph-rest-1.0) | [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) collection | Retrieve the requests for active role assignments made through the [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignmentschedulerequests?view=graph-rest-1.0) | [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) | Create a request for an active and persistent role assignment or activate, deactivate, extend, or renew an eligible role assignment. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentschedulerequest-get?view=graph-rest-1.0) | [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) | Retrieve a request for an active role assignment made through the [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) object. |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentschedulerequest-cancel?view=graph-rest-1.0) | None | Cancel a request for an active role assignment. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentschedulerequest-filterbycurrentuser?view=graph-rest-1.0) | [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) collection | Retrieve the requests for active role assignments for a particular principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | String | Represents the type of the operation on the role assignment request. The possible values are: `adminAssign`, `adminUpdate`, `adminRemove`, `selfActivate`, `selfDeactivate`, `adminExtend`, `adminRenew`, `selfExtend`, `selfRenew`, `unknownFutureValue`.  <br><br><br>- `adminAssign`: For administrators to assign roles to principals.<br>- `adminRemove`: For administrators to remove principals from roles.<br>- `adminUpdate`: For administrators to change existing role assignments.<br>- `adminExtend`: For administrators to extend expiring assignments.<br>- `adminRenew`: For administrators to renew expired assignments.<br>- `selfActivate`: For principals to activate their assignments.<br>- `selfDeactivate`: For principals to deactivate their active assignments.<br>- `selfExtend`: For principals to request to extend their expiring assignments.<br>- `selfRenew`: For principals to request to renew their expired assignments. |
| approvalId | String | The identifier of the approval of the request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| appScopeId | String | Identifier of the app-specific scope when the assignment is scoped to an app. The scope of an assignment determines the set of resources for which the principal has been granted access. App scopes are scopes that are defined and understood by this application only. Use `/` for tenant-wide app scopes. Use **directoryScopeId** to limit the scope to particular directory objects, for example, administrative units. Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| completedDateTime | DateTimeOffset | The request completion date time. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The principal that created this request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| createdDateTime | DateTimeOffset | The request creation date time. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. |
| customData | String | Free text field to define any custom data for the request. Not used. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| directoryScopeId | String | Identifier of the directory object representing the scope of the assignment. The scope of an assignment determines the set of resources for which the principal has been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. Use `/` for tenant-wide scope. Use **appScopeId** to limit the scope to an application only. Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| id | String | The unique identifier for the **unifiedRoleAssignmentScheduleRequest** object. Key, not nullable, Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| isValidationOnly | Boolean | Determines whether the call is a validation or an actual call. Only set this property if you want to check whether an activation is subject to additional rules like MFA before actually submitting the request. |
| justification | String | A message provided by users and administrators when create they create the **unifiedRoleAssignmentScheduleRequest** object. |
| principalId | String | Identifier of the principal that has been granted the assignment. Can be a user, role-assignable group, or a service principal. Supports `$filter` \(`eq`, `ne`\). |
| roleDefinitionId | String | Identifier of the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object that is being assigned to the principal. Supports `$filter` \(`eq`, `ne`\). |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | The period of the role assignment. Recurring schedules are currently unsupported. |
| status | String | The status of the role assignment request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. Supports `$filter` \(`eq`, `ne`\). |
| targetScheduleId | String | Identifier of the schedule object that's linked to the assignment request. Supports `$filter` \(`eq`, `ne`\). |
| ticketInfo | [ticketInfo](https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-1.0) | Ticket details linked to the role assignment request including details of the ticket number and ticket system. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activatedUsing | [unifiedRoleEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedule?view=graph-rest-1.0) | If the request is from an eligible administrator to activate a role, this parameter will show the related eligible assignment for that activation. Otherwise, it's `null`. Supports `$expand` and `$select` nested in `$expand`. |
| appScope | [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-1.0) | Read-only property with details of the app-specific scope when the assignment is scoped to an app. Nullable. Supports `$expand`. |
| directoryScope | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The directory object that is the scope of the assignment. Read-only. Supports `$expand`. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The principal that's getting a role assignment through the request. Supports `$expand` and `$select` nested in `$expand` for **id** only. |
| roleDefinition | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) | Detailed information for the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object that is referenced through the **roleDefinitionId** property. Supports `$expand` and `$select` nested in `$expand`. |
| targetSchedule | [unifiedRoleAssignmentSchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedule?view=graph-rest-1.0) | The schedule for an eligible role assignment that is referenced through the **targetScheduleId** property. Supports `$expand` and `$select` nested in `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleAssignmentScheduleRequest",
  "id": "String (identifier)",
  "status": "String",
  "completedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "approvalId": "String",
  "customData": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "action": "String",
  "principalId": "String",
  "roleDefinitionId": "String",
  "directoryScopeId": "String",
  "appScopeId": "String",
  "isValidationOnly": "Boolean",
  "targetScheduleId": "String",
  "justification": "String",
  "scheduleInfo": {
    "@odata.type": "microsoft.graph.requestSchedule"
  },
  "ticketInfo": {
    "@odata.type": "microsoft.graph.ticketInfo"
  }
}
```
