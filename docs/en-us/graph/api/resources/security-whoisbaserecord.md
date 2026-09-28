<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# whoisBaseRecord resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents a WHOIS entry that contains information about a registered [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0), the contacts for the registered **host**, and other metadata about the registration. This is an abstract type that can't be accessed directly. You can use the following implementation types instead:

- [whoisHistoryRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoishistoryrecord?view=graph-rest-1.0)
- [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| abuse | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **abuse** contact. |
| admin | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **admin** contact. |
| billing | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **billing** contact. |
| domainStatus | String | The domain status for this WHOIS object. |
| expirationDateTime | DateTimeOffset | The date and time when this WHOIS record expires with the registrar. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| firstSeenDateTime | DateTimeOffset | The first seen date and time of this WHOIS record. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The ID for this WHOIS record object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastSeenDateTime | DateTimeOffset | The last seen date and time of this WHOIS record. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| lastUpdateDateTime | DateTimeOffset | The date and time when this WHOIS record was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| nameservers | [microsoft.graph.security.whoisNameserver](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisnameserver?view=graph-rest-1.0) collection | The nameservers for this WHOIS object. |
| noc | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **noc** contact. |
| rawWhoisText | String | The raw WHOIS details for this WHOIS object. |
| registrant | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **registrant** contact. |
| registrar | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **registrar** contact. |
| registrationDateTime | DateTimeOffset | The date and time when this WHOIS record was registered with a registrar. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| technical | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **technical** contact. |
| whoisServer | String | The WHOIS server that provides the details. |
| zone | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **zone** contact. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| host | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | The host associated to this WHOIS object. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.whoisBaseRecord",
  "abuse": {"@odata.type": "microsoft.graph.security.whoisContact"},
  "admin": {"@odata.type": "microsoft.graph.security.whoisContact"},
  "billing": {"@odata.type": "microsoft.graph.security.whoisContact"},
  "domainStatus": "String",
  "expirationDateTime": "String (timestamp)",
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastSeenDateTime": "String (timestamp)",
  "lastUpdateDateTime": "String (timestamp)",
  "nameservers": [{"@odata.type": "microsoft.graph.security.whoisNameserver"}],
  "noc": {"@odata.type": "microsoft.graph.security.whoisContact"},
  "rawWhoisText": "String",
  "registrant": {"@odata.type": "microsoft.graph.security.whoisContact"},
  "registrar": {"@odata.type": "microsoft.graph.security.whoisContact"},
  "registrationDateTime": "String (timestamp)",
  "technical": {"@odata.type": "microsoft.graph.security.whoisContact"},
  "whoisServer": "String",
  "zone": {"@odata.type": "microsoft.graph.security.whoisContact"}
}
```
