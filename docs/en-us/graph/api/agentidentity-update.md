<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentity-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Update agentIdentity

Namespace: microsoft.graph

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

Update the properties of an [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentity.EnableDisable.All | AgentIdentity.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentity.EnableDisable.All, AgentIdentity.CreateAsManager | AgentIdentity.ReadWrite.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

### Permissions for specific scenarios

- To update the **customSecurityAttributes** property:

  - In delegated scenarios, the admin must be assigned the *Attribute Assignment Administrator* role and the app granted the *CustomSecAttributeAssignment.ReadWrite.All* and *AgentIdentity.ReadWrite.All* delegated permissions.
  - In app-only scenarios using Microsoft Graph permissions, the app must be granted the *CustomSecAttributeAssignment.ReadWrite.All* application permission.

## HTTP request

```http
PATCH /servicePrincipals/{id}/microsoft.graph.agentIdentity
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintains their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response

If successful, this method returns a `204 No Content` response code.

For information about errors returned by agent identity APIs, see [Agent identity error codes](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform/error-codes).

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/servicePrincipals/{id}/microsoft.graph.agentIdentity
Content-type: application/json

{
  "displayName": "My New Name"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
