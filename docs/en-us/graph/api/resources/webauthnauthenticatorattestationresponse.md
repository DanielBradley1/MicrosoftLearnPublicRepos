<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webauthnauthenticatorattestationresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# webauthnAuthenticatorAttestationResponse resource type

Namespace: microsoft.graph

Represents the authenticator's response to a client's request for generation of a new credential. This object contains cryptographic proof that the credential was created by a valid authenticator. This complex type is the type for the **response** property of the [webauthnPublicKeyCredential](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredential?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attestationObject | String | A CBOR-encoded attestation object containing the authenticator data and attestation statement. This value is Base64URL-encoded without padding. |
| clientDataJSON | String | Contains the JSON-compatible serialization of client data passed to the authenticator by the client. This value is Base64URL-encoded without padding. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webauthnAuthenticatorAttestationResponse",
  "clientDataJSON": "String",
  "attestationObject": "String"
}
```
