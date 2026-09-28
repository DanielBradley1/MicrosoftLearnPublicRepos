<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethodtarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# microsoftAuthenticatorAuthenticationMethodTarget resource type

Namespace: microsoft.graph

A collection of groups enabled to use [Microsoft Authenticator authentication methods policy](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethodconfiguration?view=graph-rest-1.0) in Microsoft Entra ID.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationMode | microsoftAuthenticatorAuthenticationMode | Determines which types of notifications can be used for sign-in. The possible values are: `any`, `deviceBasedPush` \(passwordless only\), `push`. |
| id | String | Object ID of a Microsoft Entra user or group. |
| isRegistrationRequired | Boolean | Determines whether the user is enforced to register the authentication method. *Not supported*. |
| targetType | authenticationMethodTargetType | The possible values are: `user`, `group`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.microsoftAuthenticatorAuthenticationMethodTarget",
  "targetType": "String",
  "id": "String (identifier)",
  "isRegistrationRequired": "Boolean",
  "authenticationMode": "String"
}
```
