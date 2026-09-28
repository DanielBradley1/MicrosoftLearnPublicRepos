<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trustedcertificateauthoritybase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-01-02 -->

# trustedCertificateAuthorityBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents a list of certificate authorities \(CAs\) that are permitted to issue certificates for authentication.

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateAuthorities | [certificateAuthority](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthority?view=graph-rest-beta) collection | Multi-value property that represents a list of trusted certificate authorities. |
| deletedDateTime | DateTimeOffset | Date and time when this object was deleted. Always `null` when the object hasn't been deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). |
| id | String | The unique identifier for the **trustedCertificateAuthorityBase** object. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trustedCertificateAuthorityBase",
  "certificateAuthorities": [{"@odata.type": "microsoft.graph.certificateAuthority"}],
  "deletedDateTime": "String (timestamp)",
  "id": "String (identifier)"
}
```
