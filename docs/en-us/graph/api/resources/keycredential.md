<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/keycredential?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# keyCredential resource type

Namespace: microsoft.graph

Contains a key credential associated with an application or a service principal. The **keyCredentials** property of the [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) and [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) entities is a collection of **keyCredential**.

To add a keyCredential using Microsoft Graph, see [Add a certificate to an app using Microsoft Graph](https://learn.microsoft.com/en-us/graph/applications-how-to-add-certificate).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customKeyIdentifier | Binary | A 40-character binary type that can be used to identify the credential. Optional. When not provided in the payload, defaults to the thumbprint of the certificate. |
| displayName | String | The friendly name for the key, with a maximum length of 90 characters. Longer values are accepted but shortened. Optional. |
| endDateTime | DateTimeOffset | The date and time at which the credential expires. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| key | Binary | The certificate's raw data in byte array converted to Base64 string. Requires `$select` to retrieve; only available for single object requests \(`GET /applications/{applicationId}?$select=keyCredentials` or `GET /servicePrincipals/{servicePrincipalId}?$select=keyCredentials`\); otherwise, it's always `null`.  <br>  <br>From a *.cer* certificate, you can read the key using the **Convert.ToBase64String\(\)** method. For more information, see [Get the certificate key](https://learn.microsoft.com/en-us/graph/applications-how-to-add-certificate). |
| keyId | Guid | The unique identifier \(GUID\) for the key. |
| startDateTime | DateTimeOffset | The date and time at which the credential becomes valid.The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| type | String | The type of key credential; for example, `Symmetric`, `AsymmetricX509Cert`. |
| usage | String | A string that describes the purpose for which the key can be used; for example, `Verify`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.keyCredential",
  "customKeyIdentifier": "Binary",
  "displayName": "String",
  "endDateTime": "String (timestamp)",
  "key": "Binary",
  "keyId": "Guid",
  "startDateTime": "String (timestamp)",
  "type": "String",
  "usage": "String"
}
```
