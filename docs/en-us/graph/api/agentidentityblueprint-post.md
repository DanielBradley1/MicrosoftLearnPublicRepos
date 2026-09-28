<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Create agentIdentityBlueprint

Namespace: microsoft.graph

Create a new [agent identity blueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprint.Create | AgentIdentityBlueprint.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprint.Create | AgentIdentityBlueprint.ReadWrite.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned one of the following roles:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)
  - [Agent ID Developer](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-developer)

## HTTP request

```http
POST /applications/microsoft.graph.agentIdentityBlueprint
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of [agent identity blueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object. You must specify the **displayName** property and **sponsors** relationship.

## Response

If successful, this method returns a `201 Created` response code and an [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object in the response body.

For information about errors returned by agent identity APIs, see [Microsoft agent identity platform error codes](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform/error-codes).

## Examples

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/applications/microsoft.graph.agentIdentityBlueprint
Content-type: application/json

{
  "displayName": "Display name",
  "sponsors@odata.bind": [
    "https://graph.microsoft.com/v1.0/users/e64405d7-f156-4ce1-b1f5-b0d801c367f3"
   ]
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applications/microsoft.graph.agentIdentityBlueprint/$entity",
    "id": "03ef14b0-ca33-4840-8f4f-d6e91916010e",
    "appId": "00001111-aaaa-2222-bbbb-3333cccc4444",
    "identifierUris": [],
    "createdDateTime": "2019-09-17T19:10:35.2742618Z",
    "displayName": "Display name",
    "publisherDomain": "contoso.com",
    "requiredResourceAccess": [],
    "signInAudience": "AzureADMyOrg"
}
```
