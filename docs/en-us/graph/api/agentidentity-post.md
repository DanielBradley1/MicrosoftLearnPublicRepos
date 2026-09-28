<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentity-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# Create agentIdentity

Namespace: microsoft.graph

Create a new [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) object from the specified [agent identity blueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentity.Create.All | AgentIdentity.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentity.Create.All | AgentIdentity.CreateAsManager, AgentIdentity.ReadWrite.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

## HTTP request

```http
POST /servicePrincipals/microsoft.graph.agentIdentity
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) object. The request body must contain **displayName**, **agentIdentityBlueprintId**, and a valid **sponsor** reference.

## Response

If successful, this method returns a `201 Created` response code and a [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) object in the response body.

For information about errors returned by agent identity APIs, see [Agent identity error codes](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform/error-codes).

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/microsoft.graph.agentIdentity
Content-type: application/json

{
  "displayName": "My Agent Identity",
  "agentIdentityBlueprintId": "65415bb1-9267-4313-bbf5-ae259732ee12",
  "sponsors@odata.bind": [
    "https://graph.microsoft.com/v1.0/users/acc9f0a1-9075-464f-9fe7-049bf1ae6481",
    "https://graph.microsoft.com/v1.0/groups/47309f33-e0ff-7be6-defe-28b504c8cd2e"
  ]
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#servicePrincipals/$entity",
    "@odata.type": "#microsoft.graph.agentIdentity",
    "id": "59e617e5-e447-4adc-8b88-00af644d7c92",
    "createdByAppId": "f98c895e-6ce2-4f5b-a31b-da7e48f25daa",
    "displayName": "My Agent Identity",
    "servicePrincipalType": "ServiceIdentity",
    "tags": [],
    "agentIdentityBlueprintId": "65415bb1-9267-4313-bbf5-ae259732ee12"
}
```
