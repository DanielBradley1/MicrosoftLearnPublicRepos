<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/assignedplan?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-03 -->

# assignedPlan resource type

Namespace: microsoft.graph

The **assignedPlans** property of both the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) entity and the [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0) entity is a collection of **assignedPlan**.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedDateTime | DateTimeOffset | The date and time at which the plan was assigned. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| capabilityStatus | String | Condition of the capability assignment. The possible values are `Enabled`, `Warning`, `Suspended`, `Deleted`, `LockedOut`. See [a detailed description](#capabilitystatus-values) of each value. |
| service | String | The name of the service; for example, `exchange`. |
| servicePlanId | Guid | A GUID that identifies the service plan. For a complete list of GUIDs and their equivalent friendly service names, see [Product names and service plan identifiers for licensing](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/licensing-service-plan-reference). |

### capabilityStatus values

The following table describes the possible statuses for the **capabilityStatus** of a subscription. The members are listed in the order of their transition if the license isn't renewed.

| Member | Description |
| :--- | :--- |
| Enabled | Available for normal use and assignment. |
| Warning | Available for normal use and assignment but is in a grace period. |
| Suspended | Unavailable for assignment but any data associated with the capability must be preserved. |
| LockedOut | Unavailable for all administrators and users for assignment but any data associated with the capability must be preserved. This is the state after `Suspended` and if the license isn't renewed, it is the final state before the plan is `Deleted`. |
| Deleted | Unavailable and any data associated with the capability may be deleted. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "assignedDateTime": "String (timestamp)",
  "capabilityStatus": "String",
  "service": "String",
  "servicePlanId": "Guid"
}
```
