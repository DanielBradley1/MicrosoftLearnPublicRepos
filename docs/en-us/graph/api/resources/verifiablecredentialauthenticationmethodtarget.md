<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialauthenticationmethodtarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-15 -->

# verifiableCredentialAuthenticationMethodTarget resource type

Namespace: microsoft.graph

A collection of groups enabled to use Verifiable Credential for identification.

Inherits from [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Object identifier of a Microsoft Entra user or group. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isRegistrationRequired | Boolean | Indicates whether the user is required to register the authentication method. Inherited from [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0). |
| targetType | authenticationMethodTargetType | The authentication method type. Inherited from [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0). The possible values are: `user`, `group`, `unknownFutureValue`. |
| verifiedIdProfiles | Guid collection | A collection of Verified ID profile IDs. The profiles define the credentials that users can present to prove their id when signing in, onboarding, or recovering. Verified ID profiles are managed through the [Verified ID APIs](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiableCredentialAuthenticationMethodTarget",
  "id": "String (identifier)",
  "targetType": "String",
  "isRegistrationRequired": "Boolean",
  "verifiedIdProfiles": [
    "Guid"
  ]
}
```
