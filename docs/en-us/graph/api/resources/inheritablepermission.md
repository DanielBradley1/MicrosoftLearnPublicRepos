<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# inheritablePermission resource type

Namespace: microsoft.graph

Defines scopes of a resource application that are configured on an [agent identity blueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) and that may be automatically granted to [agent identities](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) without additional consent. For more information, see [Configure inheritable permissions for blueprints](https://learn.microsoft.com/en-us/entra/agent-id/identity-professional/configure-inheritable-permissions-blueprints).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-list-inheritablepermissions?view=graph-rest-1.0) | [inheritablePermission](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) collection | Get a list of the inheritablePermission objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-post-inheritablepermissions?view=graph-rest-1.0) | [inheritablePermission](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) | Create a new inheritablePermission object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/inheritablepermission-get?view=graph-rest-1.0) | [inheritablePermission](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) | Read the properties and relationships of [inheritablePermission](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/inheritablepermission-update?view=graph-rest-1.0) | [inheritablePermission](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) | Update the properties of an inheritablePermission object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-delete-inheritablepermissions?view=graph-rest-1.0) | None | Delete an inheritablePermission object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inheritableScopes | [inheritableScopes](https://learn.microsoft.com/en-us/graph/api/resources/inheritablescopes?view=graph-rest-1.0) | Inheritance configuration for delegated permission scopes published by the resource application. Supports three patterns: `allAllowedScopes` \(inherit all available scopes\), `enumeratedScopes` \(inherit only the listed scopes\), and `noScopes` \(inherit none\). Each pattern exposes a `kind` discriminator for filtering. |
| resourceAppId | String | The **appId** of the resource [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) that publishes these scopes. Primary key. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.inheritablePermission",
  "resourceAppId": "String (identifier)",
  "inheritableScopes": {
    "@odata.type": "microsoft.graph.inheritableScopes"
  }
}
```
