<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-list-report?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# Get lifecyclePolicyReport

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the latest [lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-beta) for a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-AgentId.Read.All | LifecyclePolicies-AgentId.ReadWrite.All, LifecyclePolicies-Guests.Read.All, LifecyclePolicies-Guests.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-AgentId.Read.All | LifecyclePolicies-AgentId.ReadWrite.All, LifecyclePolicies-Guests.Read.All, LifecyclePolicies-Guests.ReadWrite.All |

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

If successful, this method returns a `200 OK` response code and a [lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-beta) object in the response body.

## Examples

### Request

```http
GET https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/lifecyclePolicies/37c2a69d-38d7-42ad-8b77-24da70f35bd4/report
```

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

```json
{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/lifecycleWorkflows/lifecyclePolicies('37c2a69d-38d7-42ad-8b77-24da70f35bd4')/report/$entity",
  "id": "49d50258-4a38-4d78-b740-efb1036a6547",
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
