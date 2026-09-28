<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-post-owners?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Add agentIdentityBlueprintPrincipal owners

Namespace: microsoft.graph

Add an owner for the [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0). Agent identity blueprint principal owners can be users, the agent identity blueprint principal itself, or other service principals.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprint.ReadWrite.All | Not available |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprint.ReadWrite.All | Not available |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

## HTTP request

You can address the agent identity blueprint principal using either its **id** or **appId**. **id** and **appId** are referred to as the **Object ID** and **Application \(Client\) ID**, respectively, in app registrations in the Microsoft Entra admin center.

```http
POST /servicePrincipals/{id}/microsoft.graph.agentIdentityBlueprintPrincipal/owners/$ref
POST /servicePrincipals(appId='{appId}')/microsoft.graph.agentIdentityBlueprintPrincipal/owners/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/{id}/microsoft.graph.agentIdentityBlueprintPrincipal/owners/$ref
Content-Type: application/json

{
    "@odata.id": "https://graph.microsoft.com/v1.0/directoryObjects/1511d5e7-c324-4362-ad4b-16c20076e5aa"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const directoryObject = {
    '@odata.id': 'https://graph.microsoft.com/v1.0/directoryObjects/1511d5e7-c324-4362-ad4b-16c20076e5aa'
};

await client.api('/servicePrincipals/{id}/microsoft.graph.agentIdentityBlueprintPrincipal/owners/$ref')
	.post(directoryObject);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
