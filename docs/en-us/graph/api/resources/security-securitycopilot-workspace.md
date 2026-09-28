<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-workspace?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# workspace resource type \(for securityCopilot\)

Namespace: microsoft.graph.security.securityCopilot

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Microsoft Security Copilot workspace. For more information, see [Workspaces overview](https://learn.microsoft.com/en-us/copilot/security/workspaces-overview).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/securitycopilot-list-workspaces?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.workspace](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-workspace?view=graph-rest-beta) collection | Get a list of the workspace objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the Security Copilot workspace. |
| id | String | Represents the unique ID of the Security Copilot workspace or `default` to represent the default workspace that was created as part of the initial onboarding to Security Copilot. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| plugins | [microsoft.graph.security.securityCopilot.plugin](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-plugin?view=graph-rest-beta) collection | Represents plugins in Security Copilot. |
| sessions | [microsoft.graph.security.securityCopilot.session](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-session?view=graph-rest-beta) collection | Represents sessions in Security Copilot. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.securityCopilot.workspace",
  "id": "String (identifier)",
  "displayName": "String"
}
```
