<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userpasswordresetsandchangessummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-02 -->

# userPasswordResetsAndChangesSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the summary of password resets and changes for a specific day. This summary includes the number of password resets that were self-service and those triggered by an administrator.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authenticationmethodsroot-list-userpasswordresetsandchangessummary?view=graph-rest-beta) | [userPasswordResetsAndChangesSummary](https://learn.microsoft.com/en-us/graph/api/resources/userpasswordresetsandchangessummary?view=graph-rest-beta) collection | Get a list of the userPasswordResetsAndChangesSummary objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aggregatedDateTime | DateTimeOffset | The aggregated day for which the summary applies to. This property will always represent the entire day. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| changePasswordSelfServiceCount | Int64 | The number of self-service password changes that occurred during this window. |
| id | String | Identifier for the report. |
| passwordResetsByAdminCount | Int64 | The number of admin-triggered password resets that occurred during this window. |
| passwordResetsSelfServiceCount | Int64 | The number of self-service password resets that occurred during this window. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userPasswordResetsAndChangesSummary",
  "id": "String (identifier)",
  "aggregatedDateTime": "String (timestamp)",
  "passwordResetsByAdminCount": "Integer",
  "passwordResetsSelfServiceCount": "Integer",
  "changePasswordSelfServiceCount": "Integer"
}
```
