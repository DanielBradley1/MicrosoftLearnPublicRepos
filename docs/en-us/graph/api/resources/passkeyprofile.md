<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/passkeyprofile?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# passkeyProfile resource type

Namespace: microsoft.graph

Configuration profile for [passkey \(FIDO2\) authentication method policy](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethodconfiguration?view=graph-rest-1.0) that allows for granular, group-based control over passkey configurations.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

No methods are supported.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attestationEnforcement | attestationEnforcement | Determines whether attestation must be enforced for passkey \(FIDO2\) registration. Required. The possible values are: `disabled`, `registrationOnly`, `unknownFutureValue`. |
| id | String | The passkey profile identifier. Required. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| keyRestrictions | [fido2KeyRestrictions](https://learn.microsoft.com/en-us/graph/api/resources/fido2keyrestrictions?view=graph-rest-1.0) | Controls whether key restrictions are enforced on passkeys \(FIDO2\), either allowing or disallowing certain key types as defined by Authenticator Attestation GUID \(AAGUID\), an identifier that indicates the type \(for example, make and model\) of the authenticator. Required. |
| name | String | Name of the passkey profile. Required. |
| passkeyTypes | passkeyTypes | Specifies which types of passkeys are targeted in this passkey profile. Required. The possible values are: `deviceBound`, `synced`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.passkeyProfile",
  "id": "String (identifier)",
  "name": "String",
  "passkeyTypes": "String",
  "attestationEnforcement": "String",
  "keyRestrictions": {
    "@odata.type": "microsoft.graph.fido2KeyRestrictions"
  }
}
```
