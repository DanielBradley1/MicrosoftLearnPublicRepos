<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webauthncredentialcreationoptions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# webauthnCredentialCreationOptions resource type

Namespace: microsoft.graph

Represents the options required to create a new [WebAuthn credential](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredential?view=graph-rest-1.0). This object is returned by the [fido2AuthenticationMethod: creationOptions](https://learn.microsoft.com/en-us/graph/api/fido2authenticationmethod-creationoptions?view=graph-rest-1.0) function and provides the parameters needed by the client to generate a new passkey.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| challengeTimeoutDateTime | DateTimeOffset | The date and time when the challenge times out and can no longer be used to create a credential. |
| publicKey | [webauthnPublicKeyCredentialCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialcreationoptions?view=graph-rest-1.0) | The WebAuthn public key creation options. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webauthnCredentialCreationOptions",
  "challengeTimeoutDateTime": "String (timestamp)",
  "publicKey": {
    "@odata.type": "microsoft.graph.webauthnPublicKeyCredentialCreationOptions"
  }
}
```
