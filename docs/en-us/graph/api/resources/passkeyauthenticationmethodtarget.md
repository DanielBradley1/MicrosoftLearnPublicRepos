<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/passkeyauthenticationmethodtarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# passkeyAuthenticationMethodTarget resource type

Namespace: microsoft.graph

A collection of groups that are enabled to use a passkey \(FIDO2\) authentication method as part of a passkey \(FIDO2\) authentication method policy in Microsoft Entra ID. Inherits from [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedPasskeyProfiles | Guid collection | List of passkey profiles scoped to the targets. Required. |
| id | String | Object identifier of a Microsoft Entra user or group. Required. |
| isRegistrationRequired | Boolean | Indicates whether the user is required to register the authentication method. Required. |
| targetType | authenticationMethodTargetType | The authentication method type. The possible values are: `group` and `unknownFutureValue`. Effective December 2022, the `user` target value is no longer recommended. We recommend moving individual users to a targeted group. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.passkeyAuthenticationMethodTarget",
  "id": "String",
  "targetType": "String",
  "isRegistrationRequired": "Boolean",
  "allowedPasskeyProfiles": [
    "Guid"
  ]
}
```
