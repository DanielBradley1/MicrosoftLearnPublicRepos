<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-list-report?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Get lifecyclePolicyReport

Namespace: microsoft.graph.identityGovernance

Read the latest [lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-1.0) for a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0).

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

Note

Each permissions table applies only to its specified policy subject type. Agent identity policy permissions and guest policy permissions are not interchangeable.

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/lifecyclePolicies/{lifecyclePolicyId}/report
```

## Optional query parameters

This method supports the `$select` OData query parameter to customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-1.0) object in the response body.

## Examples

### Request

```http
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/lifecyclePolicies/37c2a69d-38d7-42ad-8b77-24da70f35bd4/report
```

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/lifecyclePolicies('37c2a69d-38d7-42ad-8b77-24da70f35bd4')/report/$entity",
  "id": "37c2a69d-38d7-42ad-8b77-24da70f35bd4",
  "policyVersion": 4,
  "scopeProcessing": {
    "currentStatus": "idle",
    "currentStartedDateTime": null,
    "latestAttempt": {
      "status": "completed",
      "startedDateTime": "2026-08-08T01:00:00Z",
      "completedDateTime": "2026-08-08T01:04:12Z",
      "error": null
    },
    "lastSuccessfulProcessingDateTime": "2026-08-08T01:04:12Z"
  },
  "subjectsInScopeCount": 120
}
```
