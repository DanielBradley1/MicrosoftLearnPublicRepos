<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificateentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# sslCertificateEntity resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents an entity related to an [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0). An **sslCertificateEntity** is either an issuer or subject of the certificate.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [microsoft.graph.physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | A physical address of the entity. |
| alternateNames | String collection | Alternate names for this entity that are part of the certificate. |
| commonName | String | A common name for this entity. |
| email | String | An email for this entity. |
| givenName | String | If the entity is a person, this is the person's given name \(first name\). |
| organizationName | String | If the entity is an organization, this is the name of the organization. |
| organizationUnitName | String | If the entity is an organization, this communicates if a unit in the organization is named on the entity. |
| serialNumber | String | A serial number assigned to the entity; usually only available if the entity is the issuer. |
| surname | String | If the entity is a person, this is the person's surname \(last name\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.sslCertificateEntity",
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "alternateNames": ["String"],
  "commonName": "String",
  "email": "String",
  "givenName": "String",
  "organizationName": "String",
  "organizationUnitName": "String",
  "serialNumber": "String",
  "surname": "String"
}
```
