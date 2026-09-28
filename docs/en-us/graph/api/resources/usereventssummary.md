<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usereventssummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-12 -->

# userEventsSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a specific user MFA/SSPR registration or reset event, including whether the event was successful, which authentication method was targeted, and failure reason if any.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authenticationmethodsroot-list-usereventssummary?view=graph-rest-beta) | [userEventsSummary](https://learn.microsoft.com/en-us/graph/api/resources/usereventssummary?view=graph-rest-beta) collection | Get a list of the user registration and reset events as defined in the [userEventsSummary](https://learn.microsoft.com/en-us/graph/api/resources/usereventssummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authMethod | [usageAuthMethod](https://learn.microsoft.com/en-us/graph/api/resources/usageauthmethod?view=graph-rest-beta) | The authentication method being targeted in the event. |
| eventDateTime | DateTimeOffset | The date and time \(UTC\) when the event occurred. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| failureReason | String | The specific reason why the event failed \(if it was not successful.\) |
| feature | featureType | The type of event that occurred. The possible values are: `registration`, `reset`, `unknownFutureValue`. |
| id | String | User object identifier in Microsoft Entra ID. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isSuccess | Boolean | Indicates whether the event was successful or not. |
| userDisplayName | String | The user display name, such as `Adele Vance`. Supports `$filter` \(`eq`, `startsWith`\) and `$orderby`. |
| userPrincipalName | String | The user principal name, such as `AdeleV@contoso.com`. Supports `$filter` \(`eq`, `startsWith`\) and `$orderby`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userEventsSummary",
  "id": "String (identifier)",
  "feature": "String",
  "userPrincipalName": "String",
  "userDisplayName": "String",
  "isSuccess": "Boolean",
  "authMethod": "String",
  "failureReason": "String",
  "eventDateTime": "String (timestamp)"
}
```
