<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessscheduleinstance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# privilegedAccessScheduleInstance resource type

Namespace: microsoft.graph

An abstract type that exposes properties relating to the instances of membership and ownership assignments and eligibilities to groups that are governed by PIM. This abstract type is inherited by the following derived types:

- [privilegedAccessGroupAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentscheduleinstance?view=graph-rest-1.0)
- [privilegedAccessGroupEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityscheduleinstance?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTimeOffset | When the schedule instance ends. Required. |
| id | String | The identifier of the access assignment schedule instance. Required. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| startDateTime | DateTimeOffset | When this instance starts. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegedAccessScheduleInstance",
  "id": "String (identifier)",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)"
}
```
