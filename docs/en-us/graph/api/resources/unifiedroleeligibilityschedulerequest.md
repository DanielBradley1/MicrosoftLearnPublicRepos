<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedulerequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRoleEligibilityScheduleRequest resource type

Namespace: microsoft.graph

Represents a request for a role eligibility for a principal through PIM. The role eligibility can be permanently eligible without an expiry date or temporarily eligible with an expiry date. Inherits from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0).

For more information about PIM scenarios you can define through the **unifiedRoleEligibilityScheduleRequest** resource type, see [Overview of role management through the privileged identity management \(PIM\) API](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-1.0).

Note

To activate an eligible role assignment, use the [Create unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignmentschedulerequests?view=graph-rest-1.0) API.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roleeligibilityschedulerequests?view=graph-rest-1.0) | [unifiedRoleEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedulerequest?view=graph-rest-1.0) collection | Retrieve the requests for role eligibilities for principals made through the unifiedRoleEligibilityScheduleRequest object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleeligibilityschedulerequests?view=graph-rest-1.0) | [unifiedRoleEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedulerequest?view=graph-rest-1.0) | Request for a role eligibility for a principal through the unifiedRoleEligibilityScheduleRequest object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedroleeligibilityschedulerequest-get?view=graph-rest-1.0) | [unifiedRoleEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedulerequest?view=graph-rest-1.0) | Read the details of a request for a role eligibility request made through the unifiedRoleEligibilityScheduleRequest object. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/unifiedroleeligibilityschedulerequest-filterbycurrentuser?view=graph-rest-1.0) | [unifiedRoleEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedulerequest?view=graph-rest-1.0) collection | In PIM, retrieve the requests for role eligibilities for a particular principal. The principal can be the creator or approver of the unifiedRoleEligibilityScheduleRequest object, or they can be the target of the role eligibility. |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/unifiedroleeligibilityschedulerequest-cancel?view=graph-rest-1.0) | None | Immediately cancel a **unifiedRoleEligibilityScheduleRequest** object whose status is `Granted` and have the system automatically delete the canceled request after 30 days. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | unifiedRoleScheduleRequestActions | Represents the type of operation on the role eligibility request. The possible values are: `adminAssign`, `adminUpdate`, `adminRemove`, `selfActivate`, `selfDeactivate`, `adminExtend`, `adminRenew`, `selfExtend`, `selfRenew`, `unknownFutureValue`.  <br><br><br>- `adminAssign`: For administrators to assign eligible roles to principals.<br>- `adminRemove`: For administrators to remove eligible roles from principals.<br>- `adminUpdate`: For administrators to change existing role eligibilities.<br>- `adminExtend`: For administrators to extend expiring role eligibilities.<br>- `adminRenew`: For administrators to renew expired eligibilities.<br>- `selfActivate`: For users to activate their assignments.<br>- `selfDeactivate`: For users to deactivate their active assignments.<br>- `selfExtend`: For users to request to extend their expiring assignments.<br>- `selfRenew`: For users to request to renew their expired assignments. |
| approvalId | String | The identifier of the approval of the request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| appScopeId | String | Identifier of the app-specific scope when the role eligibility is scoped to an app. The scope of a role eligibility determines the set of resources for which the principal is eligible to access. App scopes are scopes that are defined and understood by this application only. Use `/` for tenant-wide app scopes. Use **directoryScopeId** to limit the scope to particular directory objects, for example, administrative units. Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| completedDateTime | DateTimeOffset | The request completion date time. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The principal that created this request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The request creation date time. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| customData | String | Free text field to define any custom data for the request. Not used. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| directoryScopeId | String | Identifier of the directory object representing the scope of the role eligibility. The scope of a role eligibility determines the set of resources for which the principal has been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. Use `/` for tenant-wide scope. Use **appScopeId** to limit the scope to an application only. Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| id | String | The unique identifier for the **unifiedRoleEligibilityScheduleRequest** object. Key, not nullable, Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isValidationOnly | Boolean | Determines whether the call is a validation or an actual call. Only set this property if you want to check whether an activation is subject to additional rules like MFA before actually submitting the request. |
| justification | String | A message provided by users and administrators when create they create the **unifiedRoleEligibilityScheduleRequest** object. |
| principalId | String | Identifier of the principal that has been granted the role eligibility. Can be a user or a role-assignable group. You can grant only [active assignments](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) service principals.Supports `$filter` \(`eq`, `ne`\). |
| roleDefinitionId | String | Identifier of the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object that is being assigned to the principal. Supports `$filter` \(`eq`, `ne`\). |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | The period of the role eligibility. Recurring schedules are currently unsupported. |
| status | String | The status of the role eligibility request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. Supports `$filter` \(`eq`, `ne`\). |
| targetScheduleId | String | Identifier of the schedule object that's linked to the eligibility request. Supports `$filter` \(`eq`, `ne`\). |
| ticketInfo | [ticketInfo](https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-1.0) | Ticket details linked to the role eligibility request including details of the ticket number and ticket system. Optional. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appScope | [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-1.0) | Read-only property with details of the app-specific scope when the role eligibility is scoped to an app. Nullable. Supports `$expand`. |
| directoryScope | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The directory object that is the scope of the role eligibility. Read-only. Supports `$expand`. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The principal that's getting a role eligibility through the request. Supports `$expand`. |
| roleDefinition | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) | Detailed information for the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object that is referenced through the **roleDefinitionId** property. Supports `$expand`. |
| targetSchedule | [unifiedRoleEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedule?view=graph-rest-1.0) | The schedule for a role eligibility that is referenced through the **targetScheduleId** property. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleEligibilityScheduleRequest",
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
