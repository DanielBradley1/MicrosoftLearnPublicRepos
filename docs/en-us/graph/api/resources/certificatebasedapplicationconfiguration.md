<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# certificateBasedApplicationConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a configuration of trusted certificate authorities for certificates that can be assigned to apps and service principals in the tenant.

Inherits from [trustedCertificateAuthorityAsEntityBase](https://learn.microsoft.com/en-us/graph/api/resources/trustedcertificateauthorityasentitybase?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/certificateauthoritypath-list-certificatebasedapplicationconfigurations?view=graph-rest-beta) | [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) collection | Get a list of the [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/certificateauthoritypath-post-certificatebasedapplicationconfigurations?view=graph-rest-beta) | [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) | Create a new [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/certificatebasedapplicationconfiguration-get?view=graph-rest-beta) | [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) | Read the properties and relationships of a [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/certificatebasedapplicationconfiguration-update?view=graph-rest-beta) | [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) | Update the properties of a [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and time when this object was deleted. Always `null` when the object hasn't been deleted. Inherited from [trustedCertificateAuthorityAsEntityBase](https://learn.microsoft.com/en-us/graph/api/resources/trustedcertificateauthorityasentitybase?view=graph-rest-beta). |
| description | String | The description of the trusted certificate authorities. |
| displayName | String | The display name of the trusted certificate authorities. |
| id | String | The unique identifier for the trusted certificate authorities. Inherited from [trustedCertificateAuthorityAsEntityBase](https://learn.microsoft.com/en-us/graph/api/resources/trustedcertificateauthorityasentitybase?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| trustedCertificateAuthorities | [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) collection | The collection of certificate authorities and their configuration. Inherited from [trustedCertificateAuthorityAsEntityBase](https://learn.microsoft.com/en-us/graph/api/resources/trustedcertificateauthorityasentitybase?view=graph-rest-beta). Supports `$expand`.  <br>  <br>A maximum of 10 trusted authorities are allowed in this collection. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.certificateBasedApplicationConfiguration",
  "deletedDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)"
}
```
