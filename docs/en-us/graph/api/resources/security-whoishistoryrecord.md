<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-whoishistoryrecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# whoisHistoryRecord resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents a historical WHOIS record that contains information about a registered [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0), the contacts for the registered **host**, and other metadata about the registration. Historical WHOIS records may additionally communicate details of the most recent [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0), as it is a part of the history.

Inherits from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-whoisrecord-list-history?view=graph-rest-1.0) | [microsoft.graph.security.whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) | Get a list of [whoisHistoryRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoishistoryrecord?view=graph-rest-1.0) objects for a [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0), including the properties and relationships of each [whoisHistoryRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoishistoryrecord?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-whoishistoryrecord-get?view=graph-rest-1.0) | [microsoft.graph.security.whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoishistoryrecord?view=graph-rest-1.0) | Read the properties and relationships of a [whoisHistoryRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoishistoryrecord?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| abuse | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **abuse** contact. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| admin | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **admin** contact. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| billing | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **billing** contact. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| domainStatus | String | The domain status for this WHOIS object. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| expirationDateTime | DateTimeOffset | The date and time when this WHOIS record expires with the registrar. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| firstSeenDateTime | DateTimeOffset | The first seen date and time of this WHOIS record. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| id | String | The ID for this WHOIS record object. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| lastSeenDateTime | DateTimeOffset | The last seen date and time of this WHOIS record. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| lastUpdateDateTime | DateTimeOffset | The date and time when this WHOIS record was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| nameservers | [microsoft.graph.security.whoisNameserver](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisnameserver?view=graph-rest-1.0) collection | The nameservers for this WHOIS object. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| noc | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **noc** contact. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| rawWhoisText | String | The raw WHOIS details for this WHOIS object. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| registrant | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **registrant** contact. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| registrar | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **registrar** contact. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| registrationDateTime | DateTimeOffset | The date and time when this WHOIS record was registered with a registrar. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| technical | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **technical** contact. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| whoisServer | String | The WHOIS server that provides the details. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |
| zone | [microsoft.graph.security.whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0) | The contact information for the **zone** contact. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| host | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | The host associated to this WHOIS object. Inherited from [whoisBaseRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisbaserecord?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.whoisHistoryRecord",
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
