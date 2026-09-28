<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentity-list-transitivememberof?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# List agentIdentity transitive memberships

Namespace: microsoft.graph

Get the groups and directory roles that this [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) is a member of. This operation is transitive and will include all groups that this agent identity is a nested member of.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentity.Read.All | Application.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentity.Read.All, AgentIdentity.CreateAsManager | Application.Read.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

## HTTP request

```http
GET /servicePrincipals/{id}/microsoft.graph.agentIdentity/transitiveMemberOf
```

## Optional query parameters

This method supports the `$filter`, `$count`, `$select`, `$search`, `$top` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

- OData cast is also enabled.
- `$search` is supported on the **displayName** and **description** properties only.
- The default and maximum page size is 100 and 999 objects respectively.
- The use of query parameters with this API is supported only with advanced query parameters. For more information, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/v1.0/servicePrincipals/{id}/microsoft.graph.agentIdentity/transitiveMemberOf
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let transitiveMemberOf = await client.api('/servicePrincipals/{id}/microsoft.graph.agentIdentity/transitiveMemberOf')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.group",
      "id": "id-value",
      "createdDateTime": null,
      "description": "All users at the company",
      "displayName": "All Users",
      "groupTypes": [],
      "mailEnabled": false,
      "securityEnabled": true
    }
  ]
}
```
