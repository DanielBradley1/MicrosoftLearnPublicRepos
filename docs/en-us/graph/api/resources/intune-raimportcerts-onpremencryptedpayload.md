<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-onpremencryptedpayload?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# onPremEncryptedPayload resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List onPremEncryptedPayloads](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-onpremencryptedpayload-list?view=graph-rest-beta) | [onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-onpremencryptedpayload?view=graph-rest-beta) collection | List properties and relationships of the [onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-onpremencryptedpayload?view=graph-rest-beta) objects. |
| [Get onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-onpremencryptedpayload-get?view=graph-rest-beta) | [onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-onpremencryptedpayload?view=graph-rest-beta) | Read properties and relationships of the [onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-onpremencryptedpayload?view=graph-rest-beta) object. |
| [Create onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-onpremencryptedpayload-create?view=graph-rest-beta) | [onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-onpremencryptedpayload?view=graph-rest-beta) | Create a new [onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-onpremencryptedpayload?view=graph-rest-beta) object. |
| [Delete onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-onpremencryptedpayload-delete?view=graph-rest-beta) | None | Deletes a [onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-onpremencryptedpayload?view=graph-rest-beta). |
| [Update onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-onpremencryptedpayload-update?view=graph-rest-beta) | [onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-onpremencryptedpayload?view=graph-rest-beta) | Update the properties of a [onPremEncryptedPayload](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-onpremencryptedpayload?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| tenantId | Guid |  |
| userId | Guid |  |
| deviceId | Guid |  |
| payloadId | Guid |  |
| deviceKeyThumbprint | String |  |
| cert1PayloadUUID | String |  |
| cert2PayloadUUID | String |  |
| cert3PayloadUUID | String |  |
| plistTemplate | String |  |
| encryptedBlob | Binary |  |
| payloadVersion | Int32 |  |
| status | Int32 |  |
| createdTime | DateTimeOffset |  |
| lastModifiedTime | DateTimeOffset |  |
| eTag | String |  |
| isDeleted | Boolean |  |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.onPremEncryptedPayload",
  "tenantId": "Guid",
  "userId": "Guid",
  "deviceId": "Guid",
  "payloadId": "Guid",
  "deviceKeyThumbprint": "String",
  "cert1PayloadUUID": "String",
  "cert2PayloadUUID": "String",
  "cert3PayloadUUID": "String",
  "plistTemplate": "String",
  "encryptedBlob": "binary",
  "payloadVersion": 1024,
  "status": 1024,
  "createdTime": "String (timestamp)",
  "lastModifiedTime": "String (timestamp)",
  "eTag": "String",
  "isDeleted": true
}
```
