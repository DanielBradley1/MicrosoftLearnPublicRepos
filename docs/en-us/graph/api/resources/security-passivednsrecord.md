<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# passiveDnsRecord resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents a passive DNS record. Passive DNS is a system of record that stores DNS resolution data for a given location, record, and timeframe. This historical resolution data set allows users to view which domains resolved to an IP address and vice versa. This data set allows for time-based correlation based on domain or IP overlap. Passive DNS might enable the identification of previously unknown or newly created threat actor infrastructure.

Inherits from [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get passive DNS record](https://learn.microsoft.com/en-us/graph/api/security-passivednsrecord-get?view=graph-rest-1.0) | [microsoft.graph.security.passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| collectedDateTime | DateTimeOffset | The date and time that this **passiveDnsRecord** entry was collected by Microsoft. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| firstSeenDateTime | DateTimeOffset | The date and time when this **passiveDnsRecord** entry was first seen. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The unique identifier for this **passiveDnsRecord** entry. Inherited from [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0). |
| lastSeenDateTime | DateTimeOffset | The date and time when this **passiveDnsRecord** entry was most recently seen. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| recordType | String | The DNS record type for this **passiveDnsRecord** entry. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| artifact | [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0) | The [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0) related to this **passiveDnsRecord** entry. |
| parentHost | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | The parent [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) related to this **passiveDnsRecord** entry. Generally, this is the value that you can search to discover this **passiveDnsRecord** value. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.passiveDnsRecord",
  "collectedDateTime": "String (timestamp)",
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastSeenDateTime": "String (timestamp)",
  "recordType": "String"
}
```
