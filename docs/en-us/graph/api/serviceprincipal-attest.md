<!-- Source: https://learn.microsoft.com/en-us/graph/api/serviceprincipal-attest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# servicePrincipal: attest

Namespace: microsoft.graph.identityGovernance

Attest an agent identity through its [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) to confirm it still meets the requirements of its governing [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). Attestation updates the identity's lifecycle state and can clear attestation-related compliance issues.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentity.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentity.ReadWrite.All | Not available. |

Important

For delegated access, the `AgentIdentity.ReadWrite.All` scope alone is insufficient. The signed-in user must also be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json), be a direct owner of the agent, or be a direct sponsor of the agent. *Agent Identity Administrator* is the least privileged role supported for the administrator path. Ownership and sponsorship are separate authorization paths and don't require that role.

For application access, the `AgentIdentity.ReadWrite.All` application permission grants access without an additional ownership, sponsorship, or admin-role check. These rules apply to agent attestation through either the service principal route or the agent identity cast route.

## HTTP request

```http
POST /servicePrincipals/{servicePrincipalsId}/microsoft.graph.identityGovernance.attest
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/55bc54bb-f5ef-431b-9e8f-6ee6320191fe/microsoft.graph.identityGovernance.attest
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
