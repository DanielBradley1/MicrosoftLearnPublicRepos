<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# certificateBasedAuthPki resource type

Namespace: microsoft.graph

The collection of public key infrastructure \(PKI\) instances for the [certificate-based authentication method](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmethodconfiguration?view=graph-rest-1.0). The [certificate-based authentication method](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmethodconfiguration?view=graph-rest-1.0) must be enabled in the tenant for you to manage these PKI instances.

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/publickeyinfrastructureroot-list-certificatebasedauthconfigurations?view=graph-rest-1.0) | [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) collection | Get a list of the [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/publickeyinfrastructureroot-post-certificatebasedauthconfigurations?view=graph-rest-1.0) | [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) | Create a new [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/certificatebasedauthpki-get?view=graph-rest-1.0) | [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) | Read the properties and relationships of a [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/certificatebasedauthpki-update?view=graph-rest-1.0) | [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) | Update the properties of a [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/publickeyinfrastructureroot-delete-certificatebasedauthconfigurations?view=graph-rest-1.0) | None | Delete a [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) object. |
| [Upload](https://learn.microsoft.com/en-us/graph/api/certificatebasedauthpki-upload?view=graph-rest-1.0) | None | Download the PKI file and populate the certificateAuthorities. |
| [List deleted items](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve the [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) objects deleted in the tenant in the last 30 days. |
| [Get deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a deleted [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) object by ID. |
| [Restore deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Restore a [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) object deleted in the tenant in the last 30 days. |
| [Permanently delete item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Permanently delete a deleted [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) object from the tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | The date and time when the object was soft deleted. Inherited from base class and `null` for objects that are not deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| displayName | String | The name of the object. Maximum length is 256 characters. |
| id | String | The ID of the object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the object was created or last modified. |
| status | String | The status of any asynchronous jobs runs on the object which can be upload or delete. |
| statusDetails | String | The status details of the upload/deleted operation of PKI \(Public Key Infrastructure\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| certificateAuthorities | [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) collection | The collection of certificate authorities contained in this public key infrastructure resource. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.certificateBasedAuthPki",
  "id": "String (identifier)",
  "deletedDateTime": "String (timestamp)",
  "displayName": "String",
  "status": "String",
  "statusDetails": "String",
  "lastModifiedDateTime": "String (timestamp)"
}
```
