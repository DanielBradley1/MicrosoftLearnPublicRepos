<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicypriorityconfiguration-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Update lifecyclePolicyPriorityConfiguration

Namespace: microsoft.graph.identityGovernance

Update the properties of a [lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-1.0) object to reorder the evaluation priority of lifecycle policies for a subject type.

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

## HTTP request

```http
PATCH /identityGovernance/lifecycleWorkflows/lifecyclePolicyPriorityConfigurations/{subjectType}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | The ETag of the lifecycle policy priority configuration. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| orderedPolicyIds | String collection | The ordered list of lifecycle policy IDs, from highest to lowest priority, for the subject type. Only the highest-priority matching policy binds to an identity. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/lifecyclePolicyPriorityConfigurations/agentIdentity
Content-Type: application/json
If-Match: W/"JzEtVGFncCc="

{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration",
  "orderedPolicyIds": [
    "f360e310-e2c9-4bb3-a3ca-791d3c0b6548",
    "ba9191ab-e88f-4278-942c-4dcc6a4f05b1"
  ]
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
