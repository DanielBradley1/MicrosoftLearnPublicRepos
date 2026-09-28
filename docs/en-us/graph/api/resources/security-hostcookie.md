<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# hostCookie resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents a cookie, which is a small piece of data sent from a server to a client as the user browses the internet. These values sometimes contain a state for the application or little bits of tracking data. When Microsoft Defender Threat Intelligence crawls a website, it indexes cookie names so users can search them. Cookies are also used by malicious actors to keep track of infected victims or to store data to be used later.

The **hostCookie** is associated with a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) resource.

Inherits from [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-hostcookie-get?view=graph-rest-1.0) | [microsoft.graph.security.hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| domain | String | The URI for which the cookie is valid. |
| firstSeenDateTime | DateTimeOffset | The first date and time when this **hostCookie** was observed by Microsoft Defender Threat Intelligence. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. |
| id | String | A system-generated ID for this **hostCookie**. Inherited from [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0). |
| lastSeenDateTime | DateTimeOffset | The most recent date and time when this **hostCookie** was observed by Microsoft Defender Threat Intelligence. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. |
| name | String | The name of the cookie, for example, `JSESSIONID` or `SEARCH_NAMESITE`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| host | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | Indicates that a cookie of this name and domain was found related to this host. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hostCookie",
  "domain": "String",
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastSeenDateTime": "String (timestamp)",
  "name": "String"
}
```
