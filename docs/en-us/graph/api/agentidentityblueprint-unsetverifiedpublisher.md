<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-unsetverifiedpublisher?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# agentIdentityBlueprint: unsetVerifiedPublisher

Namespace: microsoft.graph

Unset the [verifiedPublisher](https://learn.microsoft.com/en-us/graph/api/resources/verifiedpublisher?view=graph-rest-1.0) previously set on an [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0), removing all verified publisher properties. For more information, see [Publisher verification](https://learn.microsoft.com/en-us/azure/active-directory/develop/publisher-verification-overview).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprint.DeleteRestore.All | AgentIdentityBlueprint.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprint.DeleteRestore.All | AgentIdentityBlueprint.ReadWrite.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

## HTTP request

```http
POST /applications/{id}/microsoft.graph.agentIdentityBlueprint/unsetVerifiedPublisher
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/applications/{id}/microsoft.graph.agentIdentityBlueprint/unsetVerifiedPublisher
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/applications/{id}/microsoft.graph.agentIdentityBlueprint/unsetVerifiedPublisher')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
