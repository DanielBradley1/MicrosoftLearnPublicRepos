<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usermfasigninsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-02 -->

# userMfaSignInSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the total count of MFA vs non-MFA sign in counts for a given window.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authenticationmethodsroot-list-usermfasigninsummary?view=graph-rest-beta) | [userMfaSignInSummary](https://learn.microsoft.com/en-us/graph/api/resources/usermfasigninsummary?view=graph-rest-beta) collection | Get a list of the userMfaSignInSummary objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time \(UTC\) for when the summary was aggregated for. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The id for the summary. |
| multiFactorSignIns | Int64 | The total number of MFA sign-ins for the given day. |
| singleFactorSignIns | Int64 | The total number of non-MFA sign ins for the given day. |
| totalSignIns | Int64 | The total number of sign-ins for the given day. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userMfaSignInSummary",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "totalSignIns": "Integer",
  "singleFactorSignIns": "Integer",
  "multiFactorSignIns": "Integer"
}
```
