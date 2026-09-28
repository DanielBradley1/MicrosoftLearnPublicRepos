<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-04-23 -->

# authenticationMethodConfiguration resource type

Namespace: microsoft.graph

This is an abstract type that represents the settings for each authentication method. It has the configuration of whether a specific authentication method is enabled or disabled for the tenant and which users and groups can register and use that method.

The following authentication methods are derived from the **authenticationMethodConfiguration** resource type:

- [emailAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/emailauthenticationmethodconfiguration?view=graph-rest-1.0)
- [fido2AuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethodconfiguration?view=graph-rest-1.0)
- [microsoftAuthenticatorAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethodconfiguration?view=graph-rest-1.0)
- [voiceAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/voiceauthenticationmethodconfiguration?view=graph-rest-1.0)
- [smsAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/smsauthenticationmethodconfiguration?view=graph-rest-1.0)
- [softwareOathAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethodconfiguration?view=graph-rest-1.0)
- [temporaryAccessPassAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethodconfiguration?view=graph-rest-1.0)
- [x509CertificateAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmethodconfiguration?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from a policy. |
| id | String | The policy name. |
| state | authenticationMethodState | The state of the policy. The possible values are: `enabled`, `disabled`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ]
}
```
