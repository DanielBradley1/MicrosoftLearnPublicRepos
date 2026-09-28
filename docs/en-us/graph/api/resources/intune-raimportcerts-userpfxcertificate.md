<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userPFXCertificate resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that encapsulates all information required for a user's PFX certificates.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userPFXCertificates](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-userpfxcertificate-list?view=graph-rest-beta) | [userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta) collection | List properties and relationships of the [userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta) objects. |
| [Get userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-userpfxcertificate-get?view=graph-rest-beta) | [userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta) | Read properties and relationships of the [userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta) object. |
| [Create userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-userpfxcertificate-create?view=graph-rest-beta) | [userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta) | Create a new [userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta) object. |
| [Delete userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-userpfxcertificate-delete?view=graph-rest-beta) | None | Deletes a [userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta). |
| [Update userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/api/intune-raimportcerts-userpfxcertificate-update.md?view=graph-rest-beta) | [userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta) | Update the properties of a [userPFXCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the PFX certificate. |
| thumbprint | String | SHA-1 thumbprint of the PFX certificate. |
| intendedPurpose | [userPfxIntendedPurpose](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxintendedpurpose?view=graph-rest-beta) | Certificate's intended purpose from the point-of-view of deployment. Possible values are: `unassigned`, `smimeEncryption`, `smimeSigning`, `vpn`, `wifi`. |
| userPrincipalName | String | User Principal Name of the PFX certificate. |
| startDateTime | DateTimeOffset | Certificate's validity start date/time. |
| expirationDateTime | DateTimeOffset | Certificate's validity expiration date/time. |
| providerName | String | Crypto provider used to encrypt this blob. |
| keyName | String | Name of the key \(within the provider\) used to encrypt the blob. |
| paddingScheme | [userPfxPaddingScheme](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-userpfxpaddingscheme?view=graph-rest-beta) | Padding scheme used by the provider during encryption/decryption. Possible values are: `none`, `pkcs1`, `oaepSha1`, `oaepSha256`, `oaepSha384`, `oaepSha512`. |
| encryptedPfxBlob | Binary | Encrypted PFX blob. |
| encryptedPfxPassword | String | Encrypted PFX password. |
| createdDateTime | DateTimeOffset | Date/time when this PFX certificate was imported. |
| lastModifiedDateTime | DateTimeOffset | Date/time when this PFX certificate was last modified. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userPFXCertificate",
  "id": "String (identifier)",
  "thumbprint": "String",
  "intendedPurpose": "String",
  "userPrincipalName": "String",
  "startDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "providerName": "String",
  "keyName": "String",
  "paddingScheme": "String",
  "encryptedPfxBlob": "binary",
  "encryptedPfxPassword": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
