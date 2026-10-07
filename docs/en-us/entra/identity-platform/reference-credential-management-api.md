<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/reference-credential-management-api -->
<!-- Sitemap-Last-Modified: 2026-10-05 -->

# fido2AuthenticationMethod resource type

Namespace: microsoft.graph

A representation of a passkey \(FIDO2\) registered to a user. Passkey \(FIDO2\) is a sign-in authentication method.

This is a derived type that inherits from the [authenticationMethod](https://learn.microsoft.com/en-us/entra/identity-platform/authenticationmethod?view=graph-rest-1.0) resource type.

Note

This resource has a [known issue](https://learn.microsoft.com/en-us/graph/known-issues#fido2-provisioning-api-requires-self-service-setup-to-be-enabled) related to creating FIDO2 authentication methods that requires **Allow self-service setup** to be enabled in the FIDO2 authentication method policy.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/entra/fido2authenticationmethod-list?view=graph-rest-1.0) | [fido2AuthenticationMethod](https://learn.microsoft.com/en-us/entra/identity-platform/fido2authenticationmethod?view=graph-rest-1.0) collection | Retrieve a list of a user's **fido2AuthenticationMethod** objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/entra/authentication-post-fido2methods?view=graph-rest-1.0) | [fido2AuthenticationMethod](https://learn.microsoft.com/en-us/entra/identity-platform/fido2authenticationmethod?view=graph-rest-1.0) | Create a new **fido2AuthenticationMethod** object for a user. |
| [Get](https://learn.microsoft.com/en-us/entra/fido2authenticationmethod-get?view=graph-rest-1.0) | [fido2AuthenticationMethod](https://learn.microsoft.com/en-us/entra/identity-platform/fido2authenticationmethod?view=graph-rest-1.0) | Read the properties and relationships of a user's **fido2AuthenticationMethod** object. |
| [Delete](https://learn.microsoft.com/en-us/entra/fido2authenticationmethod-delete?view=graph-rest-1.0) | None | Delete a user's **fido2AuthenticationMethod** object. |
| [Creation options](https://learn.microsoft.com/en-us/entra/fido2authenticationmethod-creationoptions?view=graph-rest-1.0) | [webauthnCredentialCreationOptions](https://learn.microsoft.com/en-us/entra/identity-platform/webauthncredentialcreationoptions?view=graph-rest-1.0) | Retrieve creation options required to generate and register a passkey for a user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aaGuid | String | Authenticator Attestation GUID, an identifier that indicates the type \(such as make and model\) of the authenticator. |
| attestationCertificates | String collection | The attestation certificate or certificates attached to this passkey. |
| attestationLevel | attestationLevel | The attestation level of this passkey \(FIDO2\). The possible values are: `attested`, `notAttested`, `unknownFutureValue`. |
| createdDateTime | DateTimeOffset | The timestamp when this key was registered to the user. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/entra/identity-platform/authenticationmethod?view=graph-rest-1.0). |
| displayName | String | The display name of the key as given by the user. |
| id | String | The authentication method identifier. |
| model | String | The manufacturer-assigned model of the FIDO2 passkey. |
| passkeyType | passkeyType | The type of passkey. The possible values are: `deviceBound`, `synced`, `unknownFutureValue`. |
| publicKeyCredential | [webauthnPublicKeyCredential](https://learn.microsoft.com/en-us/entra/identity-platform/webauthnpublickeycredential?view=graph-rest-1.0) | Contains the WebAuthn public key credential information being registered. This property is used only for write requests and isn't returned on read operations. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fido2AuthenticationMethod",
  "aaGuid": "String",
  "attestationCertificates": [
    "String"
  ],
  "attestationLevel": "String",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "model": "String",
  "passkeyType": "String",
  "publicKeyCredential": {
    "@odata.type": "microsoft.graph.webauthnPublicKeyCredential"
  }
}
```
