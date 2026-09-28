<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trustedcertificateauthorityasentitybase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-31 -->

# trustedCertificateAuthorityAsEntityBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract base type that represents the trusted certificate authority types for the tenant.

Base type of [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta).

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and time when this object was deleted. Always `null` when the object hasn't been deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). |
| id | String | The unique identifier of the object. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| trustedCertificateAuthorities | [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) collection | Collection of trusted certificate authorities. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trustedCertificateAuthorityAsEntityBase",
  "deletedDateTime": "String (timestamp)",
  "id": "String (identifier)"
}
```
