<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# privilegedAccessGroupEligibilitySchedule resource type

Namespace: microsoft.graph

Represents the schedule of eligible ownership and membership to groups that are governed by PIM.

Inherits from [privilegedAccessSchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessschedule?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-eligibilityschedules?view=graph-rest-1.0) | [privilegedAccessGroupEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0) collection | Get a list of the [privilegedAccessGroupEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupeligibilityschedule-get?view=graph-rest-1.0) | [privilegedAccessGroupEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0) | Read the properties and relationships of a [privilegedAccessGroupEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0) object. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupeligibilityschedule-filterbycurrentuser?view=graph-rest-1.0) | [privilegedAccessGroupEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0) collection | Return schedules of membership and ownership eligibility requests for the calling principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessId | privilegedAccessGroupRelationships | The identifier of the membership or ownership eligibility to the group that is governed by PIM. Required. The possible values are: `owner`, `member`. Supports `$filter` \(`eq`\). |
| createdDateTime | DateTimeOffset | When the schedule was created. Optional. Inherited from [privilegedAccessSchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessschedule?view=graph-rest-1.0). |
| createdUsing | String | The identifier of the access assignment or eligibility request that creates this schedule. Optional. Inherited from [privilegedAccessSchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessschedule?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`, and on `null` values\). |
| groupId | String | The identifier of the group representing the scope of the membership or ownership eligibility through PIM for Groups. Required. Supports `$filter` \(`eq`\). |
| id | String | The identifier of the schedule. Required. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| memberType | privilegedAccessGroupMemberType | Indicates whether the assignment is derived from a group assignment. It can further imply whether the caller can manage the schedule. Required. The possible values are: `direct`, `group`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| modifiedDateTime | DateTimeOffset | When the schedule was last modified. Optional. Inherited from [privilegedAccessSchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessschedule?view=graph-rest-1.0). |
| principalId | String | The identifier of the principal whose membership or ownership eligibility is granted through PIM for Groups. Required. Supports `$filter` \(`eq`\). |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | Represents the period of the access assignment or eligibility. The scheduleInfo can represent a single occurrence or multiple recurring instances. Required. Inherited from [privilegedAccessSchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessschedule?view=graph-rest-1.0). |
| status | String | The status of the access assignment or eligibility request. The possible values are: `Canceled`, `Denied`, `Failed`, `Granted`, `PendingAdminDecision`, `PendingApproval`, `PendingProvisioning`, `PendingScheduleCreation`, `Provisioned`, `Revoked`, and `ScheduleCreated`. Not nullable. Optional. Inherited from [privilegedAccessSchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessschedule?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | References the group that is the scope of the membership or ownership eligibility through PIM for Groups. Supports `$expand`. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | References the principal that's in the scope of this membership or ownership eligibility request to the group that's governed by PIM. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegedAccessGroupEligibilitySchedule",
  "id": "String (identifier)",
  "scheduleInfo": {
    "@odata.type": "microsoft.graph.requestSchedule"
  },
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "createdUsing": "String",
  "status": "String",
  "principalId": "String",
  "accessId": "String",
  "groupId": "String",
  "memberType": "String"
}
```
