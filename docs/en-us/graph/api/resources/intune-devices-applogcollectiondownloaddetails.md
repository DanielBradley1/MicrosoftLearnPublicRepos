<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectiondownloaddetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# appLogCollectionDownloadDetails resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| downloadUrl | String | Download SAS \(Shared Access Signature\) Url for completed app log request. |
| decryptionKey | String | Decryption key that used to decrypt the log. |
| appLogDecryptionAlgorithm | [appLogDecryptionAlgorithm](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogdecryptionalgorithm?view=graph-rest-1.0) | Decryption algorithm for Content. Default is ASE256. The possible values are: `aes256`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.appLogCollectionDownloadDetails",
  "downloadUrl": "String",
  "decryptionKey": "String",
  "appLogDecryptionAlgorithm": "String"
}
```
