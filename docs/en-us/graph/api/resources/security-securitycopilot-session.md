<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-session?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# session resource type

Namespace: microsoft.graph.security.securityCopilot

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a session within a [workspace](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-workspace?view=graph-rest-beta) in Security Copilot.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-workspace-list-sessions?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.session](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-session?view=graph-rest-beta) collection | Get a list of the session objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-workspace-post-sessions?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.session](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-session?view=graph-rest-beta) | Create a new session object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-session-get?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.session](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-session?view=graph-rest-beta) | Read the properties and relationships of [microsoft.graph.security.securityCopilot.session](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-session?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-session-update?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.session](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-session?view=graph-rest-beta) | Update the properties of a session object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Created time of the session \(UTC\). |
| displayName | String | Display name for the session. |
| id | String | Represents the unique ID of the Security Copilot session. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Last modified time of the session \(UTC\). Updated when **displayName** changes. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| prompts | [microsoft.graph.security.securityCopilot.prompt](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-prompt?view=graph-rest-beta) collection | The collection of prompts in the session. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.securityCopilot.session",
  "id": "String (identifier)",
  "displayName": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)"
}
```
