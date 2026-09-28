<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-list-inheritablepermissions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# List inheritablePermission objects

Namespace: microsoft.graph

Get a list of the [inheritablePermission](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) objects and their properties for an agent identity blueprint.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprint.Read.All | Application.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprint.Read.All | Application.Read.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

## HTTP request

```http
GET /applications/{id}/microsoft.graph.agentIdentityBlueprint/inheritablePermissions
```

## Optional query parameters

This method supports the `$select` and `$filter` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [inheritablePermission](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/v1.0/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let inheritablePermissions = await client.api('/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions')
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
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applications('bc057821-f236-49d6-9f2c-1ebf43e9437a')/inheritablePermissions",
  "value": [
    {
      "resourceAppId": "00000003-0000-0000-c000-000000000000",
      "inheritableScopes": {
        "@odata.type": "microsoft.graph.enumeratedScopes",
        "kind": "enumerated",
        "scopes": [
          "User.Read",
          "Mail.Read"
        ]
      }
    },
    {
      "resourceAppId": "00000003-0000-0ff1-ce00-000000000000",
      "inheritableScopes": {
        "@odata.type": "microsoft.graph.allAllowedScopes",
        "kind": "allAllowed"
      }
    },
    {
      "resourceAppId": "a4294fb4-199a-45eb-b2bb-405ae558f61a",
      "inheritableScopes": {
        "@odata.type": "microsoft.graph.noScopes",
        "kind": "none"
      }
    }
  ]
}
```
