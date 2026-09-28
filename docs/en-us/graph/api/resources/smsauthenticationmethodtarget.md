<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/smsauthenticationmethodtarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# smsAuthenticationMethodTarget resource type

Namespace: microsoft.graph

A collection of groups enabled to use the [text message authentication methods policy](https://learn.microsoft.com/en-us/graph/api/resources/smsauthenticationmethodconfiguration?view=graph-rest-1.0) in Microsoft Entra ID.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Object ID of a Microsoft Entra user or group. |
| isRegistrationRequired | Boolean | Determines whether the user is enforced to register the authentication method. **Not supported**. |
| isUsableForSignIn | Boolean | Determines if users can use this authentication method to sign in to Microsoft Entra ID. `true` if users can use this method for primary authentication, otherwise `false`. |
| targetType | authenticationMethodTargetType | The possible values are: `user`, `group`, and `unknownFutureValue`. From December 2022, targeting individual users using `user` is no longer recommended. Existing targets remain but we recommend moving the individual users to a targeted group. Inherited from [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.smsAuthenticationMethodTarget",
  "id": "String (identifier)",
  "targetType": "String",
  "isRegistrationRequired": "Boolean",
  "isUsableForSignIn": "Boolean"
}
```
