<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-21 -->

# privilegedAccessGroupAssignmentScheduleRequest resource type

Namespace: microsoft.graph

Represents requests for operations to create, update, delete, extend, and renew a membership or ownership assignment in PIM for Groups. The privilegedAccessGroupAssignmentScheduleRequest object is also created when an authorized principal requests a just-in-time activation of an eligible access assignment to a group's membership or ownership.

Inherits from [privilegedAccessScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessschedulerequest?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-assignmentschedulerequests?view=graph-rest-1.0) | [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) collection | Get a list of the [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-post-assignmentschedulerequests?view=graph-rest-1.0) | [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) | Create a new [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupassignmentschedulerequest-get?view=graph-rest-1.0) | [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) | Read the properties and relationships of a [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) object. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupassignmentschedulerequest-filterbycurrentuser?view=graph-rest-1.0) | [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) collection | Return assignment schedule requests for the calling principal. |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupassignmentschedulerequest-cancel?view=graph-rest-1.0) | None | Cancel a pending request for a membership or ownership assignment to a group. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessId | privilegedAccessGroupRelationships | The identifier of a membership or ownership assignment relationship to the group. Required. The possible values are: `owner`, `member`, `unknownFutureValue`. |
| action | String | Represents the type of operation on the group membership or ownership assignment request. The possible values are: `adminAssign`, `adminUpdate`, `adminRemove`, `selfActivate`, `selfDeactivate`, `adminExtend`, `adminRenew`.  <br><br><br>- `adminAssign`: For administrators to assign group membership or ownership to principals.<br>- `adminRemove`: For administrators to remove principals from group membership or ownership.<br>- `adminUpdate`: For administrators to change existing group membership or ownership assignments.<br>- `adminExtend`: For administrators to extend expiring assignments.<br>- `adminRenew`: For administrators to renew expired assignments.<br>- `selfActivate`: For principals to activate their assignments.<br>- `selfDeactivate`: For principals to deactivate their active assignments. |
| approvalId | String | The identifier of the approval of the request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| completedDateTime | DateTimeOffset | The request completion date time. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The principal that created this request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| createdDateTime | DateTimeOffset | The request creation date time. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. |
| customData | String | Free text field to define any custom data for the request. Not used. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| groupId | String | The identifier of the group representing the scope of the membership or ownership assignment through PIM for Groups. Required. |
| id | String | The unique identifier for the **privilegedAccessGroupAssignmentScheduleRequest** object. Key, not nullable, Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| isValidationOnly | Boolean | Determines whether the call is a validation or an actual call. Only set this property if you want to check whether an activation is subject to additional rules like MFA before actually submitting the request. |
| justification | String | A message provided by users and administrators when they create the **privilegedAccessGroupAssignmentScheduleRequest** object. |
| principalId | String | The identifier of the principal whose membership or ownership assignment to the group is managed through PIM for Groups. Supports `$filter` \(`eq`, `ne`\). |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | The period of the group membership or ownership assignment. Recurring schedules are currently unsupported. |
| status | String | The status of the group membership or ownership assignment request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. Supports `$filter` \(`eq`, `ne`\). |
| targetScheduleId | String | The identifier of the schedule that's created from the membership or ownership assignment request. Supports `$filter` \(`eq`, `ne`\). |
| ticketInfo | [ticketInfo](https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-1.0) | Ticket details linked to the group membership or ownership assignment request including details of the ticket number and ticket system. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activatedUsing | [privilegedAccessGroupEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0) | When the request activates a membership or ownership assignment in PIM for Groups, this object represents the eligibility policy for the group. Otherwise, it is `null`. Supports `$expand`. |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | References the group that is the scope of the membership or ownership assignment request through PIM for Groups. Supports `$expand` and `$select` nested in `$expand` for select properties like **id**, **displayName**, and **mail**. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | References the principal that's in the scope of this membership or ownership assignment request through the group that's governed by PIM. Supports `$expand` and `$select` nested in `$expand` for **id** only. |
| targetSchedule | [privilegedAccessGroupEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0) | Schedule created by this request. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegedAccessGroupAssignmentScheduleRequest",
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
  "isValidationOnly": "Boolean",
  "justification": "String",
  "scheduleInfo": {
    "@odata.type": "microsoft.graph.requestSchedule"
  },
  "ticketInfo": {
    "@odata.type": "microsoft.graph.ticketInfo"
  },
  "principalId": "String",
  "accessId": "String",
  "groupId": "String",
  "targetScheduleId": "String"
}
```
