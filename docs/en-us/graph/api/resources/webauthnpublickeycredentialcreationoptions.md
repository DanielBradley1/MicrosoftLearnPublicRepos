<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialcreationoptions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# webauthnPublicKeyCredentialCreationOptions resource type

Namespace: microsoft.graph

Defines the parameters required for creating a new WebAuthn public key credential. These options specify the relying party, user information, cryptographic parameters, and authenticator selection criteria for credential creation. This complex type is the type for the **publicKey** property of the [webauthnCredentialCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/webauthncredentialcreationoptions?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attestation | String | Specifies the relying party's preference for attestation conveyance. |
| authenticatorSelection | [webauthnAuthenticatorSelectionCriteria](https://learn.microsoft.com/en-us/graph/api/resources/webauthnauthenticatorselectioncriteria?view=graph-rest-1.0) | Criteria for selecting an appropriate authenticator for credential creation. |
| challenge | String | The challenge that the authenticator must sign to prove possession of the credential. This value is Base64URL-encoded without padding. |
| excludeCredentials | [webauthnPublicKeyCredentialDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialdescriptor?view=graph-rest-1.0) collection | A list of credentials that are already registered for this user, which should be excluded from selection. |
| extensions | [webauthnAuthenticationExtensionsClientInputs](https://learn.microsoft.com/en-us/graph/api/resources/webauthnauthenticationextensionsclientinputs?view=graph-rest-1.0) | Inputs for requested WebAuthn extensions. |
| pubKeyCredParams | [webauthnPublicKeyCredentialParameters](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialparameters?view=graph-rest-1.0) collection | The cryptographic parameters that the relying party supports, in order of preference. |
| rp | [webauthnPublicKeyCredentialRpEntity](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialrpentity?view=graph-rest-1.0) | Information about the relying party \(RP\) requesting credential creation. |
| timeout | Int32 | The time, in milliseconds, that the caller is willing to wait for the operation to complete. |
| user | [webauthnPublicKeyCredentialUserEntity](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialuserentity?view=graph-rest-1.0) | Information about the user account for which the credential is being created. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webauthnPublicKeyCredentialCreationOptions",
  "rp": {
    "@odata.type": "microsoft.graph.webauthnPublicKeyCredentialRpEntity"
  },
  "user": {
    "@odata.type": "microsoft.graph.webauthnPublicKeyCredentialUserEntity"
  },
  "challenge": "String",
  "pubKeyCredParams": [
    {
      "@odata.type": "microsoft.graph.webauthnPublicKeyCredentialParameters"
    }
  ],
  "timeout": "Integer",
  "excludeCredentials": [
    {
      "@odata.type": "microsoft.graph.webauthnPublicKeyCredentialDescriptor"
    }
  ],
  "authenticatorSelection": {
    "@odata.type": "microsoft.graph.webauthnAuthenticatorSelectionCriteria"
  },
  "attestation": "String",
  "extensions": {
    "@odata.type": "microsoft.graph.webauthnAuthenticationExtensionsClientInputs"
  }
}
```
