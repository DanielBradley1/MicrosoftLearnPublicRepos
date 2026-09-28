<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-27 -->

# certificateAuthorityDetail resource type

Namespace: microsoft.graph

The properties of each certificate authority object contained in the [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) resource.

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/certificatebasedauthpki-list-certificateauthorities?view=graph-rest-1.0) | [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) collection | Get a list of the [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/certificatebasedauthpki-post-certificateauthorities?view=graph-rest-1.0) | [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) | Create a new [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/certificateauthoritydetail-get?view=graph-rest-1.0) | [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) | Read the properties and relationships of a [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/certificateauthoritydetail-update?view=graph-rest-1.0) | [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) | Update the properties of a [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/certificatebasedauthpki-delete-certificateauthorities?view=graph-rest-1.0) | None | Delete a [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object. |
| [List deleted items](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve the [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) objects deleted in the tenant in the last 30 days. |
| [Get deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a deleted [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object by ID. |
| [Restore deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Restore a [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object deleted in the tenant in the last 30 days. |
| [Permanently delete item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Permanently delete a deleted [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object from the tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificate | Binary | The public key of the certificate authority. |
| certificateAuthorityType | certificateAuthorityType | The type of certificate authority. The possible values are: `root`, `intermediate`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| certificateRevocationListUrl | String | The URL to check if the certificate is revoked. |
| createdDateTime | DateTimeOffset | The date and time when the certificate authority was created. |
| deletedDateTime | DateTimeOffset | The date and time when the certificate authority was soft deleted. Inherited from base class and `null` for objects that are not deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| deltacertificateRevocationListUrl | String | The URL to check to find out whether the certificate is revoked. |
| displayName | String | The display name of the certificate authority. |
| expirationDateTime | DateTimeOffset | The date and time when the certificate authority expires. Supports `$filter` \(`eq`\) and `$orderby`. |
| id | String | The ID of the certificate authority. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isIssuerHintEnabled | Boolean | Indicates whether the certificate picker presents the certificate authority to the user to use for authentication. Default value is `false`. Optional. |
| issuer | String | The issuer of the certificate authority. |
| issuerSubjectKeyIdentifier | String | The subject key identifier of certificate authority. |
| thumbprint | String | The thumbprint of certificate authority certificate. Supports `$filter` \(`eq`, `startswith`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.certificateAuthorityDetail",
  "id": "String (identifier)",
  "deletedDateTime": "String (timestamp)",
  "certificateAuthorityType": "String",
  "certificate": "Binary",
  "displayName": "String",
  "issuer": "String",
  "issuerSubjectKeyIdentifier": "String",
  "createdDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "thumbprint": "String",
  "certificateRevocationListUrl": "String",
  "deltacertificateRevocationListUrl": "String",
  "isIssuerHintEnabled": "Boolean"
}
```
