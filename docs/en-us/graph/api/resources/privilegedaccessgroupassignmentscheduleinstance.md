<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentscheduleinstance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# privilegedAccessGroupAssignmentScheduleInstance resource type

Namespace: microsoft.graph

Represents an instance of a provisioned membership or ownership assignment in PIM for Groups.

Inherits from [privilegedAccessScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessscheduleinstance?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-assignmentscheduleinstances?view=graph-rest-1.0) | [privilegedAccessGroupAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentscheduleinstance?view=graph-rest-1.0) collection | Get a list of the [privilegedAccessGroupAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentscheduleinstance?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupassignmentscheduleinstance-get?view=graph-rest-1.0) | [privilegedAccessGroupAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentscheduleinstance?view=graph-rest-1.0) | Read the properties and relationships of a [privilegedAccessGroupAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentscheduleinstance?view=graph-rest-1.0) object. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupassignmentscheduleinstance-filterbycurrentuser?view=graph-rest-1.0) | [privilegedAccessGroupAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentscheduleinstance?view=graph-rest-1.0) collection | Return instances of membership and ownership assignment schedules for the calling principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessId | privilegedAccessGroupRelationships | The identifier of the membership or ownership assignment relationship to the group. Required. The possible values are: `owner`, `member`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| assignmentScheduleId | String | The identifier of the [privilegedAccessGroupAssignmentSchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedule?view=graph-rest-1.0) from which this instance was created. Required. Supports `$filter` \(`eq`, `ne`\). |
| assignmentType | privilegedAccessGroupAssignmentType | Indicates whether the membership or ownership assignment is granted through activation of an eligibility or through direct assignment. Required. The possible values are: `assigned`, `activated`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| endDateTime | DateTimeOffset | When the schedule instance ends. Required. |
| groupId | String | The identifier of the group representing the scope of the membership or ownership assignment through PIM for Groups. Optional. Supports `$filter` \(`eq`\). |
| id | String | The identifier of the access assignment schedule instance. Required. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| memberType | privilegedAccessGroupMemberType | Indicates whether the assignment is derived from a group assignment. It can further imply whether the caller can manage the assignment schedule. Required. The possible values are: `direct`, `group`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| principalId | String | The identifier of the principal whose membership or ownership assignment to the group is managed through PIM for Groups. Required. Supports `$filter` \(`eq`\). |
| startDateTime | DateTimeOffset | When this instance starts. Required. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activatedUsing | [privilegedAccessGroupEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityscheduleinstance?view=graph-rest-1.0) | When the request activates a membership or ownership in PIM for Groups, this object represents the eligibility request for the group. Otherwise, it is `null`. |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | References the group that is the scope of the membership or ownership assignment through PIM for Groups. Supports `$expand`. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | References the principal that's in the scope of the membership or ownership assignment request through the group that's governed by PIM. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegedAccessGroupAssignmentScheduleInstance",
  "id": "String (identifier)",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "principalId": "String",
  "accessId": "String",
  "groupId": "String",
  "memberType": "String",
  "assignmentType": "String",
  "assignmentScheduleId": "String"
}
```
