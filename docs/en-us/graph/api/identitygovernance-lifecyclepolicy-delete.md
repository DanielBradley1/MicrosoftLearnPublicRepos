<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Delete lifecyclePolicy

Namespace: microsoft.graph.identityGovernance

Delete a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) object. This is a soft-delete operation: the policy can be restored with the [restore](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-restore?view=graph-rest-1.0) action and appears under the deleted items container until it's permanently removed.

To permanently delete a policy, use the deleted items path. A permanently deleted policy can't be restored.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

### Agent identity policies

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-AgentId.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-AgentId.ReadWrite.All | Not available. |

### Guest policies

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-Guests.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-Guests.ReadWrite.All | Not available. |

Important

For guest lifecycle policy writes, delegated access requires both the `LifecyclePolicies-Guests.ReadWrite.All` scope and a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). *Lifecycle Workflows Administrator* is the least privileged role supported for this operation. Scope alone or role alone is insufficient.

Application access requires the `LifecyclePolicies-Guests.ReadWrite.All` application permission, without an additional user directory-role requirement. These requirements apply to creating, updating, deleting, restoring, and permanently deleting guest policies, and to changing guest policy priority. They don't describe authorization for agent policies or guest user attestation.

Note

Each permissions table applies only to its specified policy subject type. Agent identity policy permissions and guest policy permissions are not interchangeable.

## HTTP request

```http
DELETE /identityGovernance/lifecycleWorkflows/lifecyclePolicies/{lifecyclePolicyId}
DELETE /identityGovernance/lifecycleWorkflows/deletedItems/lifecyclePolicies/{lifecyclePolicyId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/lifecyclePolicies/ba9191ab-e88f-4278-942c-4dcc6a4f05b1
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
