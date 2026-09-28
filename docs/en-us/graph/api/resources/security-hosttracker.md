<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# hostTracker resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents a unique code or value found within web pages and often used to track user interaction. These codes can be used to correlate a disparate group of websites to a central entity. Often, actors copy the source code of a victim’s website they want to impersonate for a phishing campaign. Seldomly, actors take the time to remove these IDs. Actors might also deploy tracker IDs to see how successful their cyberattack campaigns are. This is similar to marketers using SEO IDs, such as a Google Analytics Tracker ID, to track the success of their marketing campaign.

The **hostTracker** is associated with a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) resource.

Inherits from [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-hosttracker-get?view=graph-rest-1.0) | [microsoft.graph.security.hostTracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.hostTracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| firstSeenDateTime | DateTimeOffset | The first date and time when this **hostTracker** was observed by Microsoft Defender Threat Intelligence. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. |
| id | String | A system-generated ID for this **hostTracker**. Inherited from [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0). |
| kind | String | The kind of **hostTracker** that was detected. For example, `GoogleAnalyticsID` or `JarmHash`. |
| lastSeenDateTime | DateTimeOffset | The most recent date and time when this **hostTracker** was observed by Microsoft Defender Threat Intelligence. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. |
| value | String | The identification value for the **hostTracker**. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| host | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | The [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) related to this **hostTracker**. When navigating to a **hostTracker** from a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0), this should be assumed to be a return reference. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hostTracker",
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "kind": "String",
  "lastSeenDateTime": "String (timestamp)",
  "value": "String"
}
```
