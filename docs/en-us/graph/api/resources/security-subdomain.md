<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-subdomain?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# subdomain resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents an internet domain that is part of a primary domain. For example, learn.microsoft.com is a subdomain of microsoft.com.

For every subdomain, there can be a new set of IP addresses to which the domain resolves. This can be a great data source for finding related infrastructure.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-subdomain-get?view=graph-rest-1.0) | [microsoft.graph.security.subdomain](https://learn.microsoft.com/en-us/graph/api/resources/security-subdomain?view=graph-rest-1.0) | Read the properties and relationships of a [subdomain](https://learn.microsoft.com/en-us/graph/api/resources/security-subdomain?view=graph-rest-1.0) object. |
| [List](https://learn.microsoft.com/en-us/graph/api/security-host-list-subdomains?view=graph-rest-1.0) | [microsoft.graph.security.subdomain](https://learn.microsoft.com/en-us/graph/api/resources/security-subdomain?view=graph-rest-1.0) collection | Get a list of **subdomain** resources of a host. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| firstSeenDateTime | DateTimeOffset | The date and time when Microsoft Defender Threat Intelligence first observed the subdomain. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | A system-generated ID for the subdomain. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| host | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | The host of the subdomain. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.subdomain",
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)"
}
```
