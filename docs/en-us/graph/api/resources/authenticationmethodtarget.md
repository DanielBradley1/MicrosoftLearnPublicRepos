<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# authenticationMethodTarget resource type

Namespace: microsoft.graph

A collection of groups that are enabled to use an authentication method as part of an authentication method policy in Microsoft Entra ID.

The following types are derived from this resource type:

- [microsoftAuthenticatorAuthenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethodtarget?view=graph-rest-1.0)
- [smsAuthenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/smsauthenticationmethodtarget?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Object Id of a Microsoft Entra user or group. |
| isRegistrationRequired | Boolean | Determines if the user is enforced to register the authentication method. |
| targetType | authenticationMethodTargetType | The possible values are: `user`, `group`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationMethodTarget",
  "id": "String (identifier)",
  "isRegistrationRequired": "Boolean",
  "targetType": "String"
}
```
