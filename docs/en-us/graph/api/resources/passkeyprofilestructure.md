<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/passkeyprofilestructure?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# passkeyProfileStructure resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Informs policy evaluation which [passkey profiles](https://learn.microsoft.com/en-us/graph/api/resources/passkeyprofile?view=graph-rest-beta) a user is in scope of.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attestationEnforcement | attestationEnforcement | Determines whether attestation must be enforced for FIDO2 passkey registration. Required. The possible values are: `disabled`, `registrationOnly`, `unknownFutureValue`. |
| id | String | The passkey profile identifier. Required. |
| isAttestationEnforced | Boolean | Determines whether attestation must be enforced for FIDO2 passkey registration. Required. |
| keyRestrictions | [fido2KeyRestrictions](https://learn.microsoft.com/en-us/graph/api/resources/fido2keyrestrictions?view=graph-rest-beta) | Controls whether key restrictions are enforced on FIDO2 passkeys, either allowing or disallowing certain key types as defined by Authenticator Attestation GUID \(AAGUID\), an identifier that indicates the type \(for example, make and model\) of the authenticator. Required. |
| name | String | Name of the passkey profile. Required. |
| passkeyTypes | passkeyTypes | Specifies which types of passkeys are targeted in this passkey profile. Required. The possible values are: `deviceBound`, `synced`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.passkeyProfileStructure",
  "id": "String",
  "name": "String",
  "passkeyTypes": "String",
  "isAttestationEnforced": "Boolean",
  "attestationEnforcement": "String",
  "keyRestrictions": {
    "@odata.type": "microsoft.graph.fido2KeyRestrictions"
  }
}
```
