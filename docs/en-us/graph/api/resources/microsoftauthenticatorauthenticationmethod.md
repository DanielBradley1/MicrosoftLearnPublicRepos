<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-28 -->

# microsoftAuthenticatorAuthenticationMethod resource type

Namespace: microsoft.graph

A representation of the Microsoft Authenticator app registered to a user. Microsoft Authenticator is an authentication method.

This type that inherits from the [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) resource type.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/microsoftauthenticatorauthenticationmethod-list?view=graph-rest-1.0) | [microsoftAuthenticatorAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethod?view=graph-rest-1.0) collection | Get a list of the [microsoftAuthenticatorAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethod?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/microsoftauthenticatorauthenticationmethod-get?view=graph-rest-1.0) | [microsoftAuthenticatorAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethod?view=graph-rest-1.0) | Read the properties and relationships of a [microsoftAuthenticatorAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethod?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/microsoftauthenticatorauthenticationmethod-delete?view=graph-rest-1.0) | None | Deletes a [microsoftAuthenticatorAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethod?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time that this app was registered. This property is null if the device isn't registered for passwordless Phone Sign-In. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0). |
| deviceTag | String | Tags containing app metadata. |
| displayName | String | The name of the device on which this app is registered. |
| id | String | A unique identifier for this authentication method. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) |
| phoneAppVersion | String | Numerical version of this instance of the Authenticator app. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| device | [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) | The registered device on which Microsoft Authenticator resides. This property is null if the device isn't registered for passwordless Phone Sign-In. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.microsoftAuthenticatorAuthenticationMethod",
  "id": "String (Identifier)",
  "displayName": "String",
  "deviceTag": "String",
  "phoneAppVersion": "String",
  "createdDateTime": "DateTimeOffset"
}
```
