<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagementschedule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-05 -->

# entitlementManagementSchedule resource type

Namespace: microsoft.graph

The entitlement management schedule is used in three scenarios in [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0). First, when a user creates an access package assignment request, the request can include a schedule for when the user wants an assignment. Second, an access package assignment that results from such a request also has a schedule. Third, the `entitlementManagementSchedule` is also used in the [accessPackageAssignmentReviewSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentreviewsettings?view=graph-rest-1.0) of an assignment policy, to specify when the first access review starts and how often access reviews should reoccur.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expiration | [expirationPattern](https://learn.microsoft.com/en-us/graph/api/resources/expirationpattern?view=graph-rest-1.0) | When the access should expire. |
| recurrence | [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) | The recurring access review pattern. Not used in access requests. |
| startDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entitlementManagementSchedule",
  "expiration": {
    "@odata.type": "microsoft.graph.expirationPattern"
  },
  "recurrence": {
    "@odata.type": "microsoft.graph.patternedRecurrence"
  },
  "startDateTime": "String (timestamp)"
}
```
