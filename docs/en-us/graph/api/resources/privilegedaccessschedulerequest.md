<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessschedulerequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# privilegedAccessScheduleRequest resource type

Namespace: microsoft.graph

An abstract type that exposes properties used to configure access eligibility and assignment in privileged identity management \(PIM\) governance operations for groups.

This is an abstract type from which the [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) and [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) resource types inherit.

Inherits from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | String | Represents the type of operation on the group membership or ownership assignment request. The possible values are: `adminAssign`, `adminUpdate`, `adminRemove`, `selfActivate`, `selfDeactivate`, `adminExtend`, `adminRenew`.  <br><br><br>- `adminAssign`: For administrators to assign group membership or ownership to principals.<br>- `adminRemove`: For administrators to remove principals from group membership or ownership.<br>- `adminUpdate`: For administrators to change existing group membership or ownership assignments.<br>- `adminExtend`: For administrators to extend expiring assignments.<br>- `adminRenew`: For administrators to renew expired assignments.<br>- `selfActivate`: For principals to activate their assignments.<br>- `selfDeactivate`: For principals to deactivate their active assignments. |
| approvalId | String | The identifier of the approval of the request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| completedDateTime | DateTimeOffset | The request completion date time. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The principal that created this request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| createdDateTime | DateTimeOffset | The request creation date time. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. |
| customData | String | Free text field to define any custom data for the request. Not used. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| id | String | The unique identifier for the **privilegedAccessGroupAssignmentScheduleRequest** object. Key, not nullable, Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| isValidationOnly | Boolean | Determines whether the call is a validation or an actual call. Only set this property if you want to check whether an activation is subject to additional rules like MFA before actually submitting the request. |
| justification | String | A message provided by users and administrators when create they create the **privilegedAccessGroupAssignmentScheduleRequest** object. |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | The period of the group membership or ownership assignment. Recurring schedules are currently unsupported. |
| status | String | The status of the group membership or ownership assignment request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. Supports `$filter` \(`eq`, `ne`\). |
| ticketInfo | [ticketInfo](https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-1.0) | Ticket details linked to the group membership or ownership assignment request including details of the ticket number and ticket system. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegedAccessScheduleRequest",
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
  }
}
```
