<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# privilegedAccessGroupEligibilityScheduleRequest resource type

Namespace: microsoft.graph

Represents requests for operations to create, update, delete, extend, and renew group membership and ownership eligibility in PIM for Groups.

Inherits from [privilegedAccessScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessschedulerequest?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-eligibilityschedulerequests?view=graph-rest-1.0) | [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) collection | Get a list of the [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-post-eligibilityschedulerequests?view=graph-rest-1.0) | [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) | Create a new [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupeligibilityschedulerequest-get?view=graph-rest-1.0) | [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) | Read the properties and relationships of a [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) object. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupeligibilityschedulerequest-filterbycurrentuser?view=graph-rest-1.0) | [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) collection | Return eligibility schedule requests for the calling principal. |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupeligibilityschedulerequest-cancel?view=graph-rest-1.0) | None | Cancel membership or ownership eligibility schedule requests for the calling principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessId | privilegedAccessGroupRelationships | The identifier of membership or ownership eligibility relationship to the group. Required. The possible values are: `owner`, `member`, `unknownFutureValue`. |
| action | String | Represents the type of operation on the group membership or ownership eligibility assignment request. The possible values are: `adminAssign`, `adminUpdate`, `adminRemove`, `selfActivate`, `selfDeactivate`, `adminExtend`, `adminRenew`.  <br><br><br>- `adminAssign`: For administrators to assign group membership or ownership eligibility to principals.<br>- `adminRemove`: For administrators to remove principals from group membership or ownership eligibilities.<br>- `adminUpdate`: For administrators to change existing eligible assignments.<br>- `adminExtend`: For administrators to extend expiring eligible assignments.<br>- `adminRenew`: For administrators to renew expired eligible assignments.<br>- `selfActivate`: For principals to activate their eligible assignments.<br>- `selfDeactivate`: For principals to deactivate their eligible assignments. |
| approvalId | String | The identifier of the approval of the request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| completedDateTime | DateTimeOffset | The request completion date time. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The principal that created this request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| createdDateTime | DateTimeOffset | The request creation date time. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. |
| customData | String | Free text field to define any custom data for the request. Not used. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). |
| groupId | String | The identifier of the group representing the scope of the membership and ownership eligibility through PIM for Groups. Required. |
| id | String | The unique identifier for the **privilegedAccessGroupEligibilityScheduleRequest** object. Key, not nullable, read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| isValidationOnly | Boolean | Determines whether the call is a validation or an actual call. Only set this property if you want to check whether an activation is subject to additional rules like MFA before actually submitting the request. |
| justification | String | A message provided by users and administrators when they create the **privilegedAccessGroupEligibilityScheduleRequest** object. |
| principalId | String | The identifier of the principal whose membership or ownership eligibility to the group is managed through PIM for Groups. Required. |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | The period of the group membership or ownership assignment. Recurring schedules are currently unsupported. |
| status | String | The status of the group membership or ownership assignment request. Inherited from [request](https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0). Read-only. Supports `$filter` \(`eq`, `ne`\). |
| targetScheduleId | String | The identifier of the schedule that's created from the eligibility request. Optional. |
| ticketInfo | [ticketInfo](https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-1.0) | Ticket details linked to the group membership or ownership assignment request including details of the ticket number and ticket system. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | References the group that is the scope of the membership or ownership eligibility request through PIM for Groups. Supports `$expand` and `$select` nested in `$expand` for select properties like **id**, **displayName**, and **mail**. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | References the principal that's in the scope of the membership or ownership eligibility request through the group that's governed by PIM. Supports `$expand` and `$select` nested in `$expand` for **id** only. |
| targetSchedule | [privilegedAccessGroupEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0) | Schedule created by this request. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegedAccessGroupEligibilityScheduleRequest",
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
