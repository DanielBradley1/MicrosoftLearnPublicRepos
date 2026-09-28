<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/passwordlessmicrosoftauthenticatorauthenticationmethod?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-27 -->

# passwordlessMicrosoftAuthenticatorAuthenticationMethod resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A representation of a Microsoft Authenticator Passwordless Phone Sign-in method registered to a user.

This is a derived type that inherits from the [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-beta) resource type.

Caution

The Microsoft Authenticator Passwordless Phone Sign-in method API is deprecated and will stop returning results on December 31, 2020. Please use the new [Microsoft Authenticator Authentication Method](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethod?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/passwordlessmicrosoftauthenticatorauthenticationmethod-list?view=graph-rest-beta) \(deprecated\) | [passwordlessMicrosoftAuthenticatorAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/passwordlessmicrosoftauthenticatorauthenticationmethod?view=graph-rest-beta) collection | Retrieve a list of a user's passwordlessMicrosoftAuthenticatorAuthenticationMethod objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/passwordlessmicrosoftauthenticatorauthenticationmethod-get?view=graph-rest-beta) \(deprecated\) | [passwordlessMicrosoftAuthenticatorAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/passwordlessmicrosoftauthenticatorauthenticationmethod?view=graph-rest-beta) | Read the properties and relationships of a user's passwordlessMicrosoftAuthenticatorAuthenticationMethod object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/passwordlessmicrosoftauthenticatorauthenticationmethod-delete?view=graph-rest-beta) \(deprecated\) | None | Deletes a user's passwordlessMicrosoftAuthenticatorAuthenticationMethod object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The authentication method identifier. |
| displayName | String | The display name of the mobile device as given by the user. |
| creationDateTime | DateTimeOffset | The timestamp when this method was registered to the user. |

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.passwordlessMicrosoftAuthenticatorAuthenticationMethod",
  "id": "String (identifier)",
  "displayName": "String",
  "creationDateTime": "String (timestamp)"
}
```
