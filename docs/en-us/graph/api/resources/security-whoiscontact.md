<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# whoisContact resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents details about a specific contact entry within a [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [microsoft.graph.physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The physical address of the entity. |
| email | String | The email of this WHOIS contact. |
| fax | String | The fax of this WHOIS contact. No format is guaranteed. |
| name | String | The name of this WHOIS contact. |
| organization | String | The organization of this WHOIS contact. |
| telephone | String | The telephone of this WHOIS contact. No format is guaranteed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.whoisContact",
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "email": "String",
  "fax": "String",
  "name": "String",
  "organization": "String",
  "telephone": "String"
}
```
