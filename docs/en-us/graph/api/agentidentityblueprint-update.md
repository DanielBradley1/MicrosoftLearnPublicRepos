<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-03 -->

# Update agentIdentityBlueprint

Namespace: microsoft.graph

Update the properties of an [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprint.AddRemoveCreds.All, AgentIdentityBlueprint.UpdateBranding.All | AgentIdentityBlueprint.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprint.AddRemoveCreds.All, AgentIdentityBlueprint.UpdateBranding.All | AgentIdentityBlueprint.ReadWrite.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

### Permissions for specific scenarios

- The least privileged permission to update credential-related properties such as **keyCredentials** and **passwordCredentials** is *AgentIdentityBlueprint.AddRemoveCreds.All*.
- The least privileged permission to update branding properties such as **displayName** and **description** is *AgentIdentityBlueprint.UpdateBranding.All*.
- To update properties covered by both permission scopes, use the higher-privileged *AgentIdentityBlueprint.ReadWrite.All* permission.

## HTTP request

```http
PATCH /applications/{id}/microsoft.graph.agentIdentityBlueprint
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

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/applications/{id}/microsoft.graph.agentIdentityBlueprint
Content-Type: application/json

{
  "displayName": "My New Name"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const agentIdentityBlueprint = {
  displayName: 'My New Name'
};

await client.api('/applications/{id}/microsoft.graph.agentIdentityBlueprint')
	.update(agentIdentityBlueprint);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
