<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-21 -->

# privilegedAccessGroup resource type

Namespace: microsoft.graph

The entry point for all resources related to Privileged Identity Management \(PIM\) for groups.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of an object in PIM governance for a group. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignmentScheduleInstances | [privilegedAccessGroupAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentscheduleinstance?view=graph-rest-1.0) collection | The instances of assignment schedules to activate a just-in-time access. |
| assignmentScheduleRequests | [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) collection | The schedule requests for operations to create, update, delete, extend, and renew an assignment. |
| assignmentSchedules | [privilegedAccessGroupAssignmentSchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedule?view=graph-rest-1.0) collection | The assignment schedules to activate a just-in-time access. |
| eligibilityScheduleInstances | [privilegedAccessGroupEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityscheduleinstance?view=graph-rest-1.0) collection | The instances of eligibility schedules to activate a just-in-time access. |
| eligibilityScheduleRequests | [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) collection | The schedule requests for operations to create, update, delete, extend, and renew an eligibility. |
| eligibilitySchedules | [privilegedAccessGroupEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedule?view=graph-rest-1.0) collection | The eligibility schedules to activate a just-in-time access. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegedAccessGroup",
  "id": "String (identifier)"
}
```
