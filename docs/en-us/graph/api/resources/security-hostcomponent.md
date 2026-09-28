<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# hostComponent resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents a web component that provides details about a web page or server infrastructure gleaned from a web crawl or scan. This information can be used to detect bad actors or sites that are compromised. It can also help users understand whether a site is vulnerable to a specific attack or compromise.

A host component is associated with a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) resource.

Inherits from [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-hostcomponent-get?view=graph-rest-1.0) | [microsoft.graph.security.hostComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.hostComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | String | The type of component that was detected \(for example, `Operating System`, `Framework`, `Remote Access`, or `Server`\). |
| firstSeenDateTime | DateTimeOffset | The first date and time when Microsoft Defender Threat Intelligence observed this web component. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. |
| id | String | A system-generated ID for this **hostComponent**. Inherited from [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0). |
| lastSeenDateTime | DateTimeOffset | The most recent date and time when Microsoft Defender Threat Intelligence observed this web component. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. |
| name | String | A name running on the artifact, for example, `Microsoft IIS`. |
| version | String | The component version running on the artifact, for example, `v8.5`. This shouldn't be assumed to be strictly numerical. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| host | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | The **host** related to this component. This is a reverse navigation property. When navigating to components from a **host**, this should be assumed to be a return reference. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hostComponent",
  "category": "String",
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastSeenDateTime": "String (timestamp)",
  "name": "String",
  "version": "String"
}
```
