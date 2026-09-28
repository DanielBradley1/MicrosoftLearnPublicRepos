<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/passwordauthenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-28 -->

# passwordAuthenticationMethod resource type

Namespace: microsoft.graph

A representation of a user's password. For security, the password itself will never be returned in the object, but action can be taken to reset a password.

This is a derived type that inherits from the [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) resource type.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authentication-list-passwordmethods?view=graph-rest-1.0) | [passwordAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/passwordauthenticationmethod?view=graph-rest-1.0) collection | Read the properties and relationships of a user's **passwordAuthenticationMethod** objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/passwordauthenticationmethod-get?view=graph-rest-1.0) | [passwordAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/passwordauthenticationmethod?view=graph-rest-1.0) | Read the properties and relationships of a user's **passwordAuthenticationMethod** object. |
| [Reset](https://learn.microsoft.com/en-us/graph/api/authenticationmethod-resetpassword?view=graph-rest-1.0) | None | Reset a user's password in the cloud and, if synced, on-premises. |
| [Get long running operation](https://learn.microsoft.com/en-us/graph/api/longrunningoperation-get?view=graph-rest-1.0) | None | Get the status of the password reset long running operation if the reset operation returned a **Location** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when this password was last updated. This property is currently not populated. Read-only. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0). |
| id | String | The identifier of this password registered to this user. This is generally `28c10230-6103-485e-b985-444c60001490`. Read-only. |
| password | String | For security, the password is always returned as `null` from a LIST or GET operation. |

## Relationships

None. The following JSON representation shows the resource type.

## JSON representation

The following is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.passwordAuthenticationMethod",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "password": "String"
}
```
