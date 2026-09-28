<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredential?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# webauthnPublicKeyCredential resource type

Namespace: microsoft.graph

Represents a WebAuthn public key credential created during FIDO2 passkey registration. This complex type is the type for the **publicKeyCredential** property of the [fido2AuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethod?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientExtensionResults | [webauthnAuthenticationExtensionsClientOutputs](https://learn.microsoft.com/en-us/graph/api/resources/webauthnauthenticationextensionsclientoutputs?view=graph-rest-1.0) | The output of the WebAuthn extension processing. |
| id | String | The credential ID created by the WebAuthn Authenticator. This value is Base64URL-encoded without padding. |
| response | [webauthnAuthenticatorAttestationResponse](https://learn.microsoft.com/en-us/graph/api/resources/webauthnauthenticatorattestationresponse?view=graph-rest-1.0) | The response from the WebAuthn Authenticator after generating an attestation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webauthnPublicKeyCredential",
  "id": "String",
  "response": {
    "@odata.type": "microsoft.graph.webauthnAuthenticatorAttestationResponse"
  },
  "clientExtensionResults": {
    "@odata.type": "microsoft.graph.webauthnAuthenticationExtensionsClientOutputs"
  }
}
```
