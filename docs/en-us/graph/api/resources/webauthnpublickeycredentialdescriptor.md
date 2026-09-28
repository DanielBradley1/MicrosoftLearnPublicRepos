<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialdescriptor?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# webauthnPublicKeyCredentialDescriptor resource type

Namespace: microsoft.graph

Describes a credential that is already registered to a user. This information is used to prevent the user from registering the same authenticator multiple times. This complex type is the type for each item in the **excludeCredentials** collection of the [webauthnPublicKeyCredentialCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialcreationoptions?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The credential ID of the credential being described. This value is Base64URL-encoded without padding. |
| transports | String collection | A hint about the types of transport that the authenticator supports. Possible values include: `usb`, `nfc`, `ble`, `internal`. |
| type | String | The type of credential. Currently, the only supported value is `public-key`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webauthnPublicKeyCredentialDescriptor",
  "type": "String",
  "id": "String",
  "transports": [
    "String"
  ]
}
```
