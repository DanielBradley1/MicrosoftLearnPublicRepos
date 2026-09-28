<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# requestSchedule resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), users who want to get access package assignments create access package assignment requests. This request can include a schedule for when the user would like to have an assignment. An access package assignment that results from such a request also has a schedule.

In [PIM for Microsoft Entra roles](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-1.0) and [PIM for Groups](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagement-for-groups-api-overview?view=graph-rest-1.0), use this resource to define the schedule for when the principal will have an eligible or active role assignment.

In entitlement management, this object is configured in the **schedule** property of:

- [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0)
- [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0)
- [accessPackageAssignmentRequestRequirements](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestrequirements?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expiration | [expirationPattern](https://learn.microsoft.com/en-us/graph/api/resources/expirationpattern?view=graph-rest-1.0) | When the eligible or active assignment expires. |
| recurrence | [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) | The frequency of the eligible or active assignment. This property is currently unsupported in PIM. |
| startDateTime | DateTimeOffset | When the eligible or active assignment becomes active. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.requestSchedule",
  "startDateTime": "String (timestamp)",
  "expiration": {
    "@odata.type": "microsoft.graph.expirationPattern"
  },
  "recurrence": {
    "@odata.type": "microsoft.graph.patternedRecurrence"
  }
}
```
