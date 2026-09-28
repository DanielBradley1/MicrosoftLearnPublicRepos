<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# artifact resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents an abstract entity found online by Microsoft security services.

Current types of artifacts include:

- [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0)

  - [hostname](https://learn.microsoft.com/en-us/graph/api/resources/security-hostname?view=graph-rest-1.0)
  - [ipAddresss](https://learn.microsoft.com/en-us/graph/api/resources/security-ipaddress?view=graph-rest-1.0)

- [hostComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0)
- [hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0)
- [hostTracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0)
- [passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0)
- [unclassifiedArtifact](https://learn.microsoft.com/en-us/graph/api/resources/security-unclassifiedartifact?view=graph-rest-1.0)

Instances of **artifact** identified in the following Microsoft Security API groups should handle the possible implementations. Microsoft Security APIs that currently support the **artifact** type:

- [Threat intelligence](https://learn.microsoft.com/en-us/graph/api/resources/security-threatintelligence?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **artifact**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.artifact",
  "id": "String (identifier)"
}
```
