<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/selfsignedcertificate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# selfSignedCertificate resource type

Namespace: microsoft.graph

Contains the public part of a signing certificate.

This resource type is the return type of the [addSelfSignedSigningCertificate](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addtokensigningcertificate?view=graph-rest-1.0) action. Service providers use the public part of the signing certificate to validate the issuer of the token.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customKeyIdentifier | Binary | Custom key identifier. |
| displayName | String | The friendly name for the key. |
| endDateTime | DateTimeOffset | The date and time at which the credential expires. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on January 1, 2014 is `2014-01-01T00:00:00Z`. |
| key | Binary | The value for the key credential. Should be a Base-64 encoded value. |
| keyId | Guid | The unique identifier \(GUID\) for the key. |
| startDateTime | DateTimeOffset | The date and time at which the credential becomes valid. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on January 1, 2014 is `2014-01-01T00:00:00Z`. |
| type | String | The type of key credential. `AsymmetricX509Cert`. |
| usage | String | A string that describes the purpose for which the key can be used. The possible value is `Verify`. |
| thumbprint | String | The thumbprint value for the key. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.selfSignedCertificate",
  "customKeyIdentifier": "String (Binary)",
  "displayName": "String",
  "endDateTime": "String (timestamp)",
  "key": "String (Binary)",
  "keyId": "Guid",
  "startDateTime": "String (timestamp)",
  "thumbprint": "String",
  "type": "String",
  "usage": "String"
}
```
