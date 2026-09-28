<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxusercertificate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# pfxUserCertificate resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List pfxUserCertificates](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-pfxusercertificate-list?view=graph-rest-beta) | [pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxusercertificate?view=graph-rest-beta) collection | List properties and relationships of the [pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxusercertificate?view=graph-rest-beta) objects. |
| [Get pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-pfxusercertificate-get?view=graph-rest-beta) | [pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxusercertificate?view=graph-rest-beta) | Read properties and relationships of the [pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxusercertificate?view=graph-rest-beta) object. |
| [Create pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-pfxusercertificate-create?view=graph-rest-beta) | [pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxusercertificate?view=graph-rest-beta) | Create a new [pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxusercertificate?view=graph-rest-beta) object. |
| [Delete pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-pfxusercertificate-delete?view=graph-rest-beta) | None | Deletes a [pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxusercertificate?view=graph-rest-beta). |
| [Update pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-pfxusercertificate-update?view=graph-rest-beta) | [pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxusercertificate?view=graph-rest-beta) | Update the properties of a [pfxUserCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxusercertificate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| tenantId | Guid |  |
| userId | Guid |  |
| thumbprint | String |  |
| userUpn | String |  |
| encryptedPfxBlob | String |  |
| encryptedPfxPassword | String |  |
| certStartDate | DateTimeOffset |  |
| certExpirationDate | DateTimeOffset |  |
| providerName | String |  |
| encryptionKeyName | String |  |
| paddingScheme | Int32 |  |
| status | Int32 |  |
| intendedPurpose | Int32 |  |
| createdTime | DateTimeOffset |  |
| isDeleted | Boolean |  |
| lastModifiedTime | DateTimeOffset |  |
| eTag | String |  |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.pfxUserCertificate",
  "tenantId": "Guid",
  "userId": "Guid",
  "thumbprint": "String",
  "userUpn": "String",
  "encryptedPfxBlob": "String",
  "encryptedPfxPassword": "String",
  "certStartDate": "String (timestamp)",
  "certExpirationDate": "String (timestamp)",
  "providerName": "String",
  "encryptionKeyName": "String",
  "paddingScheme": 1024,
  "status": 1024,
  "intendedPurpose": 1024,
  "createdTime": "String (timestamp)",
  "isDeleted": true,
  "lastModifiedTime": "String (timestamp)",
  "eTag": "String"
}
```
