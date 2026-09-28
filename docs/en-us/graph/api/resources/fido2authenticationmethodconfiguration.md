<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# fido2AuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Represents a FIDO2 authentication methods policy. Authentication methods policies define configuration settings and users or groups who are enabled to use the authentication method.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/fido2authenticationmethodconfiguration-get?view=graph-rest-1.0) | [fido2AuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethodconfiguration?view=graph-rest-1.0) | Read the properties and relationships of a fido2AuthenticationMethodConfiguration object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/fido2authenticationmethodconfiguration-update?view=graph-rest-1.0) | None | Update the properties of a fido2AuthenticationMethodConfiguration object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/fido2authenticationmethodconfiguration-delete?view=graph-rest-1.0) | None | Reverts the fido2AuthenticationMethodConfiguration object to its default configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultPasskeyProfile | String | The non-deletable baseline passkey profile, within the passkey profile collection. It's automatically created when migrating to passkey profiles and initially mirrors the tenant's legacy global passkey \(FIDO2\) authentication methods policy settings. |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. |
| id | String | The authentication method policy identifier. |
| isAttestationEnforced | Boolean | Determines whether attestation must be enforced for passkey \(FIDO2\) registration. This property is deprecated and will be removed in October 2027. Use **passkeyProfiles** property. |
| isSelfServiceRegistrationAllowed | Boolean | Determines if users can register new passkeys \(FIDO2\). |
| keyRestrictions | [fido2KeyRestrictions](https://learn.microsoft.com/en-us/graph/api/resources/fido2keyrestrictions?view=graph-rest-1.0) | Controls whether key restrictions are enforced on passkeys \(FIDO2\), either allowing or disallowing certain key types as defined by Authenticator Attestation GUID \(AAGUID\), an identifier that indicates the type \(for example, make and model\) of the authenticator. This property is deprecated and will be removed in October 2027. Use the **passkeyProfiles** property. |
| state | authenticationMethodState | The possible values are: `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [passkeyAuthenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/passkeyauthenticationmethodtarget?view=graph-rest-1.0) collection | A collection of groups that are enabled to use the authentication method. |
| passkeyProfiles | [passkeyProfile](https://learn.microsoft.com/en-us/graph/api/resources/passkeyprofile?view=graph-rest-1.0) collection | A collection of configuration profiles that control the registration of and authentication with passkeys \(FIDO2\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fido2AuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
  "defaultPasskeyProfile": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ],
  "isSelfServiceRegistrationAllowed": "Boolean",
  "isAttestationEnforced": "Boolean",
  "keyRestrictions": {
    "@odata.type": "microsoft.graph.fido2KeyRestrictions"
  },
  "includeTargets": [ { "@odata.type": "microsoft.graph.passkeyAuthenticationMethodTarget" } ]
}
```
