<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webauthnauthenticatorselectioncriteria?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# webauthnAuthenticatorSelectionCriteria resource type

Namespace: microsoft.graph

Specifies criteria for selecting an appropriate authenticator for credential creation. These criteria help ensure that the created credential meets the relying party's security and usability requirements. This complex type is the type for the **authenticatorSelection** property of the [webauthnPublicKeyCredentialCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialcreationoptions?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticatorAttachment | String | Specifies the preferred attachment modality for the authenticator. Possible values: `platform` \(device-bound authenticator, such as Windows Hello\), `cross-platform` \(removable authenticator, such as a USB security key\), or `null` \(no preference\). |
| requireResidentKey | Boolean | Indicates whether the authenticator must create a client-side-resident credential \(also known as a discoverable credential\). If `true`, the credential can be used without providing a credential ID. |
| userVerification | String | Specifies the relying party's preference for user verification during credential creation. Possible values: `required`, `preferred`, or `discouraged`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webauthnAuthenticatorSelectionCriteria",
  "authenticatorAttachment": "String",
  "requireResidentKey": "Boolean",
  "userVerification": "String"
}
```
