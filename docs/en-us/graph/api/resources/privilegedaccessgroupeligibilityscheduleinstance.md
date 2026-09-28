<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityscheduleinstance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# privilegedAccessGroupEligibilityScheduleInstance resource type

Namespace: microsoft.graph

Represents an instance of a provisioned membership or ownership eligibility in PIM for Groups.

Inherits from [privilegedAccessScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessscheduleinstance?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-eligibilityscheduleinstances?view=graph-rest-1.0) | [privilegedAccessGroupEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityscheduleinstance?view=graph-rest-1.0) collection | Get a list of the [privilegedAccessGroupEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityscheduleinstance?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupeligibilityscheduleinstance-get?view=graph-rest-1.0) | [privilegedAccessGroupEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityscheduleinstance?view=graph-rest-1.0) | Read the properties and relationships of a [privilegedAccessGroupEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityscheduleinstance?view=graph-rest-1.0) object. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupeligibilityscheduleinstance-filterbycurrentuser?view=graph-rest-1.0) | [privilegedAccessGroupEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityscheduleinstance?view=graph-rest-1.0) collection | Return instances of membership and ownership eligibility schedules for the calling principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessId | privilegedAccessGroupRelationships | The identifier of the membership or ownership eligibility relationship to the group. Required. The possible values are: `owner`, `member`. Supports `$filter` \(`eq`\). |
| eligibilityScheduleId | String | The identifier of the [privilegedAccessGroupEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0) from which this instance was created. Required. Supports `$filter` \(`eq`, `ne`\). |
| endDateTime | DateTimeOffset | When the schedule instance ends. Required. |
| groupId | String | The identifier of the group representing the scope of the membership or ownership eligibility through PIM for Groups. Required. Supports `$filter` \(`eq`\). |
| id | String | The identifier of the access assignment schedule instance. Required. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| memberType | privilegedAccessGroupMemberType | Indicates whether the assignment is derived from a group assignment. It can further imply whether the calling principal can manage the assignment schedule. Required. The possible values are: `direct`, `group`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| principalId | String | The identifier of the principal whose membership or ownership eligibility to the group is managed through PIM for Groups. Required. Supports `$filter` \(`eq`\). |
| startDateTime | DateTimeOffset | When this instance starts. Required. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | References the group that is the scope of the membership or ownership eligibility through PIM for Groups. Supports `$expand`. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | References the principal that's in the scope of the membership or ownership eligibility request through the group that's governed by PIM. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegedAccessGroupEligibilityScheduleInstance",
  "id": "String (identifier)",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "principalId": "String",
  "accessId": "String",
  "groupId": "String",
  "memberType": "String",
  "eligibilityScheduleId": "String"
}
```
