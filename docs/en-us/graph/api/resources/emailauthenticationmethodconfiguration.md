<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/emailauthenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# emailAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Represents this tenant's email OTP authentication methods policy. Authentication methods policies define configuration settings and users or groups who are enabled to use the authentication method. The tenant's cloud-native users may use email OTP for self-service password reset. External users may use email OTP for authentication during invitation redemption and self-service sign up for specific apps in user flows.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/emailauthenticationmethodconfiguration-get?view=graph-rest-1.0) | [emailAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/emailauthenticationmethodconfiguration?view=graph-rest-1.0) | Read the properties and relationships of an emailAuthenticationMethodConfiguration object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/emailauthenticationmethodconfiguration-update?view=graph-rest-1.0) | [emailAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/emailauthenticationmethodconfiguration?view=graph-rest-1.0) | Update the properties of an emailAuthenticationMethodConfiguration object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/emailauthenticationmethodconfiguration-delete?view=graph-rest-1.0) | None | Deletes an emailAuthenticationMethodConfiguration object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowExternalIdToUseEmailOtp | externalEmailOtpState | Determines whether email OTP is usable by external users for authentication. The possible values are: `default`, `enabled`, `disabled`, `unknownFutureValue`. Tenants in the `default` state who didn't use public preview have email OTP enabled beginning in October 2021. |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. |
| id | String | The authentication method policy identifier. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). |
| state | authenticationMethodState | Indicates whether this authentication method is enabled or not. The possible values are: `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0) collection | A collection of groups that are enabled to use the authentication method. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.emailAuthenticationMethodConfiguration",
  "allowExternalIdToUseEmailOtp": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ],
  "id": "String (identifier)",
  "includeTargets": [ { "@odata.type": "microsoft.graph.authenticationMethodTarget" } ],
  "state": "String"
}
```
