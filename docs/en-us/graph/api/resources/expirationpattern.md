<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/expirationpattern?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# expirationPattern resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), a user creates an access package assignment request to obtain an access package assignment. This request can include a schedule for when the user would like to have an assignment. An access package assignment that results from such a request also has a schedule. The **expiration** field of a [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) indicates when the access package assignment should expire.

In PIM, use this resource to define when a [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) or [unifiedRoleEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedulerequest?view=graph-rest-1.0) object expires. The settings allowed for this object are dependent on the [settings for the Microsoft Entra role](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-list-rules?view=graph-rest-1.0). For example, if the settings of the Microsoft Entra role specifies that permanent eligible assignments aren't allowed, specifying `noExpiration` for the **type** property returns an error.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| duration | Duration | The requestor's desired duration of access represented in ISO 8601 format for durations. For example, PT3H refers to three hours. If specified in a request, **endDateTime** should not be present and the **type** property should be set to `afterDuration`. |
| endDateTime | DateTimeOffset | Timestamp of date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| type | [expirationPatternType](#expirationpatterntype-values) | The requestor's desired expiration pattern type. The possible values are: `notSpecified`, `noExpiration`, `afterDateTime`, `afterDuration`. |

### expirationPatternType values

| Member | Description |
| :--- | :--- |
| notSpecified | No expiration schedule was specified. |
| noExpiration | The requestor did not wish the access to expire. |
| afterDateTime | Access will expire after a specified date and time. |
| afterDuration | Access will expire after a specified duration relative to access being granted. Required when the **duration** property is specified. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.expirationPattern",
  "duration": "String (duration)",
  "endDateTime": "String (timestamp)",
  "type": "String"
}
```
