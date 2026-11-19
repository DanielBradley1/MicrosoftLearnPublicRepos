<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/configure-inheritable-permissions-blueprints -->
<!-- Sitemap-Last-Modified: 2026-05-22 -->

# Configure inheritable permissions for agent identity blueprints

Configure inheritable permissions on an agent identity blueprint to specify which delegated scopes can be inherited by agent identities. A scope is eligible for inheritance only when the resource app is configured as inheritable and the scope is granted to the blueprint principal.

For conceptual background on how inheritable permissions relate to required resource access and direct permission grants, see [Inheritable permissions and required resource access](https://learn.microsoft.com/en-us/entra/agent-id/concept-inheritable-permissions).

## Prerequisites

- An existing agent identity blueprint.
- For Microsoft Graph requests, the `AgentIdentityBlueprint.Create` permission to add an entry and `AgentIdentityBlueprint.ReadWrite.All` to update or delete an entry.
- For delegated requests by a nonowner, the Agent ID Administrator role. Blueprint owners can manage their own blueprints.

## How inheritable permissions work

The public Microsoft Graph beta `inheritablePermission` resource documents delegated scope inheritance through `inheritableScopes`. The broader Agent ID permission model also describes application-role inheritance, but the public Graph reference doesn't define an application-role property or payload. Confirm the supported Graph API contract before relying on application-role inheritance.

For inheritance conditions and the distinction between declarations and grants, see [Inheritable permissions and required resource access](https://learn.microsoft.com/en-us/entra/agent-id/concept-inheritable-permissions) and the [Microsoft Graph `inheritablePermission` resource](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-beta&preserve-view=true).

## Inheritance patterns

The Graph beta API supports these patterns for delegated permission scopes:

| Pattern | Graph type | Description |
| --- | --- | --- |
| All allowed scopes | `allAllowedScopes` | Make all delegated scopes published by the resource app eligible for inheritance. |
| Enumerated scopes | `enumeratedScopes` | Make only the listed delegated scopes eligible for inheritance. |
| No scopes | `noScopes` | Disable delegated scope inheritance for the resource app. |

## Inheritable permissions limitations

The public Microsoft Graph reference doesn't specify a maximum number of resource apps or `inheritablePermissions` entries for a blueprint. Don't rely on a numeric limit unless Microsoft publishes or confirms it.

The public Graph reference also doesn't document how application roles are configured for inheritance. The API examples in this article are limited to delegated scopes.

Regularly review the scopes configured on each blueprint and the grants on its blueprint principal. Remove permissions that are no longer needed.

## Configure scope inheritance \(using Microsoft Graph\)

These examples use the Microsoft Graph beta API. Beta APIs are subject to change and aren't supported for production applications. For details, see the Microsoft Graph [create](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-post-inheritablepermissions?view=graph-rest-beta&preserve-view=true), [update](https://learn.microsoft.com/en-us/graph/api/inheritablepermission-update?view=graph-rest-beta&preserve-view=true), and [delete](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-delete-inheritablepermissions?view=graph-rest-beta&preserve-view=true) operations.

Use the `inheritablePermissions` navigation property on the `agentIdentityBlueprint` application resource. Each entry specifies scope inheritance for one resource app. When specifying `resourceAppId`, use the resource app's application ID in GUID format.

### Add all delegated scopes for Microsoft Graph

```http
POST https://graph.microsoft.com/beta/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions
Content-Type: application/json

{
  "resourceAppId": "00000003-0000-0000-c000-000000000000",
  "inheritableScopes": {
    "@odata.type": "microsoft.graph.allAllowedScopes"
  }
}
```

The request returns `201 Created`. The response includes the configured resource app and inheritance pattern:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "resourceAppId": "00000003-0000-0000-c000-000000000000",
  "inheritableScopes": {
    "@odata.type": "microsoft.graph.allAllowedScopes",
    "kind": "allAllowed"
  }
}
```

### Add enumerated scopes for a resource app

To allow only selected delegated scopes, use the `enumeratedScopes` pattern:

```http
POST https://graph.microsoft.com/beta/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions
Content-Type: application/json

{
  "resourceAppId": "00000003-0000-0000-c000-000000000000",
  "inheritableScopes": {
    "@odata.type": "microsoft.graph.enumeratedScopes",
    "scopes": [
      "User.Read",
      "Mail.Read"
    ]
  }
}
```

### Add scopes for multiple resource apps

Create a separate entry for each resource app, using its application ID as `resourceAppId`. For example, change the ID to the SharePoint Online resource app ID for a separate request:

```http
POST https://graph.microsoft.com/beta/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions
Content-Type: application/json

{
  "resourceAppId": "00000003-0000-0ff1-ce00-000000000000",
  "inheritableScopes": {
    "@odata.type": "microsoft.graph.allAllowedScopes"
  }
}
```

### Disable scope inheritance

Use `PATCH` to update an existing entry. This example disables delegated scope inheritance for Microsoft Graph:

```http
PATCH https://graph.microsoft.com/beta/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions/00000003-0000-0000-c000-000000000000
Content-Type: application/json

{
  "inheritableScopes": {
    "@odata.type": "microsoft.graph.noScopes"
  }
}
```

The update operation returns `204 No Content` when successful. To remove an entry, use `DELETE`:

```http
DELETE https://graph.microsoft.com/beta/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions/00000003-0000-0000-c000-000000000000
```

## Related content

- [Inheritable permissions and required resource access](https://learn.microsoft.com/en-us/entra/agent-id/concept-inheritable-permissions)
- [Create an agent identity from your blueprint](https://learn.microsoft.com/en-us/entra/agent-id/create-delete-agent-identities)
- [Microsoft Entra roles and permissions for agent identities](https://learn.microsoft.com/en-us/entra/agent-id/authorization-agent-id#microsoft-entra-roles-allowed-for-agents)
- [OAuth 2.0 and OpenID Connect protocols on the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols)
