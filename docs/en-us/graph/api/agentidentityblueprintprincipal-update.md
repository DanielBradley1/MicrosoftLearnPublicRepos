<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update agentIdentityBlueprintPrincipal

Namespace: microsoft.graph

Update the properties of an [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) object.

Important

- Agent identity blueprint principals inherit specific properties from their associated agent identity blueprint registrations. These properties are synchronized from the agent identity blueprint registration, but the synchronization isn't immediate or continuous. Sometimes, updating an agent identity blueprint principal may prompt the directory to refresh properties from the agent identity blueprint registration, causing updates that weren't part of the original request.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprintPrincipal.EnableDisable.All | AgentIdentityBlueprintPrincipal.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprintPrincipal.EnableDisable.All | AgentIdentityBlueprintPrincipal.ReadWrite.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

### Permissions for specific scenarios

- To update the **customSecurityAttributes** property:

  - In delegated scenarios, the admin must be assigned the *Attribute Assignment Administrator* role and the app granted the *CustomSecAttributeAssignment.ReadWrite.All* delegated permission.
  - In app-only scenarios using Microsoft Graph permissions, the app must be granted the *CustomSecAttributeAssignment.ReadWrite.All* application permission.

## HTTP request

```http
PATCH /servicePrincipals/{id}/microsoft.graph.agentIdentityBlueprintPrincipal
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintains their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

Provide the updated property values for the agent identity blueprint principal.

## Response

If successful, this method returns a `204 No Content` response code.

For information about errors returned by agent identity APIs, see [Agent identity error codes](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform/error-codes).

## Example

### Request

The following example shows a request to update an agent identity blueprint principal.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/servicePrincipals/{id}/microsoft.graph.agentIdentityBlueprintPrincipal
Content-type: application/json

{
  "appRoleAssignmentRequired": true
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const agentIdentityBlueprintPrincipal = {
  appRoleAssignmentRequired: true
};

await client.api('/servicePrincipals/{id}/microsoft.graph.agentIdentityBlueprintPrincipal')
	.update(agentIdentityBlueprintPrincipal);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
