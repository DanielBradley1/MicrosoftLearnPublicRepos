<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# certificateAuthorityAsEntity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a trusted certificate authority.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/certificatebasedapplicationconfiguration-list-trustedcertificateauthorities?view=graph-rest-beta) | [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) collection | Get a list of the [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/certificatebasedapplicationconfiguration-post-trustedcertificateauthorities?view=graph-rest-beta) | [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) | Create a new [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/certificateauthorityasentity-get?view=graph-rest-beta) | [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) | Read the properties and relationships of a [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/certificateauthorityasentity-update?view=graph-rest-beta) | [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) | Update the properties of a [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/certificateauthorityasentity-delete?view=graph-rest-beta) | None | Delete a [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificate | Binary | The trusted certificate. |
| id | String | The unique identifier for the certificate authority. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isRootAuthority | Boolean | Indicates if the certificate is a root authority. In a [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) object, at least one object in the **trustedCertificateAuthorities** collection must be a root authority. |
| issuer | String | The issuer of the trusted certificate. |
| issuerSubjectKeyIdentifier | String | The subject key identifier of the trusted certificate. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.certificateAuthorityAsEntity",
  "certificate": "String (binary)",
  "id": "String (identifier)",
  "isRootAuthority": "Boolean",
  "issuer": "String",
  "issuerSubjectKeyIdentifier": "String"
}
```
