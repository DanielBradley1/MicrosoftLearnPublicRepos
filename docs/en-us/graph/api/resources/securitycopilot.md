<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/securitycopilot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# securityCopilot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the resources related to Microsoft Security Copilot. This resource is an abstract type.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Represents the unique ID of the Security Copilot workspace. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| workspaces | [workspace](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-workspace?view=graph-rest-beta) collection | References a workspace in Security Copilot. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.securityCopilot",
  "id": "String (identifier)"
}
```
