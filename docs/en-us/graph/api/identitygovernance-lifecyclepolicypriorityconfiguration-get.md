<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicypriorityconfiguration-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Get lifecyclePolicyPriorityConfiguration

Namespace: microsoft.graph.identityGovernance

Read the properties and relationships of a [microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-1.0) object. The configuration is keyed by subject type and returns the evaluation order of lifecycle policies for that subject type.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

### Agent identity policies

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-AgentId.Read.All | LifecyclePolicies-AgentId.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-AgentId.Read.All | LifecyclePolicies-AgentId.ReadWrite.All |

### Guest policies

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-Guests.Read.All | LifecyclePolicies-Guests.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-Guests.Read.All | LifecyclePolicies-Guests.ReadWrite.All |

Important

For guest lifecycle policy reads, delegated access requires both a `LifecyclePolicies-Guests.Read.All` or `LifecyclePolicies-Guests.ReadWrite.All` scope and a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). *Global Reader* is the least privileged role supported for this operation. Lifecycle Workflows Administrator is also supported. Scope alone or role alone is insufficient.

Application access requires either corresponding application permission, without an additional user directory-role requirement. These requirements also apply to guest policy rules, reports, versions, priority configurations, and deleted policies. They don't describe authorization for agent policies or guest user lifecycle reads.

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/lifecyclePolicyPriorityConfigurations/{subjectType}
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/lifecyclePolicyPriorityConfigurations/agentIdentity
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration",
  "id": "agentIdentity",
  "subjectType": "agentIdentity",
  "orderedPolicyIds": [
    "ba9191ab-e88f-4278-942c-4dcc6a4f05b1",
    "f360e310-e2c9-4bb3-a3ca-791d3c0b6548"
  ]
}
```
