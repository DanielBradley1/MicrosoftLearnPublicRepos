<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprintprincipal-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Get agentIdentityBlueprintPrincipal

Namespace: microsoft.graph

Read the properties and relationships of [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprintPrincipal.Read.All | Application.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprintPrincipal.Read.All | Application.Read.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

## HTTP request

You can address the agent identity blueprint principal using either its **id** or **appId**.

```http
GET /servicePrincipals/{id}/microsoft.graph.agentIdentityBlueprintPrincipal
GET /servicePrincipals(appId='{appId}')/microsoft.graph.agentIdentityBlueprintPrincipal
```

## Optional query parameters

This method supports the `$count`, `$expand`, `$filter`, `$orderby`, `$search`, `$select`, and `$top` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response. Some queries are supported only when you use the **ConsistencyLevel** header set to `eventual` and `$count`. For more information, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

By default, this API doesn't return the public key value of the **key** in the **keyCredentials** property unless **keyCredentials** is specified in a `$select` query. For example, `$select=id,appId,keyCredentials`.

The use of `$select` to get **keyCredentials** for agent blueprint principals has a throttling limit of 150 requests per minute for every tenant.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept-Language | Language code. Optional. |

Providing the **Accept-Language** header with a supported language code, such as `es-ES` or `de-DE`, returns localized values where available.

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/v1.0/servicePrincipals/{id}/microsoft.graph.agentIdentityBlueprintPrincipal
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let agentIdentityBlueprintPrincipal = await client.api('/servicePrincipals/{id}/microsoft.graph.agentIdentityBlueprintPrincipal')
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
    "@odata.type": "microsoft.graph.agentIdentityBlueprintPrincipal",
    "id": "f7c938db-8c3d-4d04-937b-456c3242ed95",
    "appId": "00001111-aaaa-2222-bbbb-3333cccc4444",
    "createdDateTime": "2019-09-17T19:10:35.2742618Z",
    "accountEnabled": true,
    "appDisplayName": "My Sample App",
    "appOwnerOrganizationId": "aaaabbbb-0000-cccc-1111-dddd2222eeee",
    "appRoleAssignmentRequired": false,
    "appRoles": [],
    "disabledByMicrosoftStatus": null,
    "info": {
        "termsOfServiceUrl": null,
        "supportUrl": null,
        "privacyStatementUrl": null,
        "marketingUrl": null,
        "logoUrl": null
    },
    "oauth2PermissionScopes": [],
    "servicePrincipalType": "Application",
    "tags": [],
    "verifiedPublisher": null
}
```
