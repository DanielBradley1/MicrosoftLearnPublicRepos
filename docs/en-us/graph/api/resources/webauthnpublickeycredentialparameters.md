<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialparameters?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# webauthnPublicKeyCredentialParameters resource type

Namespace: microsoft.graph

Represents a cryptographic algorithm and credential type that the relying party supports. The relying party provides a list of these parameters in order of preference during credential creation. This complex type is the type for each item in the **pubKeyCredParams** collection of the [webauthnPublicKeyCredentialCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialcreationoptions?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alg | Int32 | A COSE algorithm identifier representing the cryptographic algorithm to use for this credential type. For example, `-7` represents ES256. |
| type | String | The type of credential to create. Currently, the only supported value is `public-key`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webauthnPublicKeyCredentialParameters",
  "type": "String",
  "alg": "Integer"
}
```
