<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessschedule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# privilegedAccessSchedule resource type

Namespace: microsoft.graph

An abstract type that exposes properties relating to the schedule of assigned and eligible membership and ownership to groups that are governed by PIM. This abstract type is inherited by the following derived types:

- [privilegedAccessGroupAssignmentSchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedule?view=graph-rest-1.0)
- [privilegedAccessGroupEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | When the schedule was created. Optional. |
| createdUsing | String | The identifier of the access assignment or eligibility request that created this schedule. Optional. |
| id | String | The identifier of the schedule. Required. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| modifiedDateTime | DateTimeOffset | When the schedule was last modified. Optional. |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | Represents the period of the access assignment or eligibility. The scheduleInfo can represent a single occurrence or multiple recurring instances. Required. |
| status | String | The status of the access assignment or eligibility request. The possible values are: `Canceled`, `Denied`, `Failed`, `Granted`, `PendingAdminDecision`, `PendingApproval`, `PendingProvisioning`, `PendingScheduleCreation`, `Provisioned`, `Revoked`, and `ScheduleCreated`. Not nullable. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegedAccessSchedule",
  "id": "String (identifier)",
  "scheduleInfo": {
    "@odata.type": "microsoft.graph.requestSchedule"
  },
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "createdUsing": "String",
  "status": "String"
}
```
