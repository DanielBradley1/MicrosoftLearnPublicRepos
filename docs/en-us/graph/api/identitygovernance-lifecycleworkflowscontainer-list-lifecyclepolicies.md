<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-lifecyclepolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# List lifecyclePolicies

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) objects and their properties in the [lifecycle workflows container](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflowscontainer?view=graph-rest-beta). Use `$filter` on the **policySource** property to distinguish system-managed default policies from user-created policies.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-AgentId.Read.All | LifecyclePolicies-AgentId.ReadWrite.All, LifecyclePolicies-Guests.Read.All, LifecyclePolicies-Guests.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-AgentId.Read.All | LifecyclePolicies-AgentId.ReadWrite.All, LifecyclePolicies-Guests.Read.All, LifecyclePolicies-Guests.ReadWrite.All |

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/lifecyclePolicies
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

If successful, this method returns a `200 OK` response code and a collection of [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/lifecyclePolicies?$filter=policySource eq 'systemDefault'
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.identityGovernance.agentIdentityLifecyclePolicy",
      "id": "00000000-0000-0000-0000-000000000001",
      "displayName": "Default agent attestation policy",
      "policySource": "systemDefault",
      "isEnabled": true,
      "versionNumber": 1,
      "enforcementAction": {
        "@odata.type": "#microsoft.graph.identityGovernance.disableThenDeleteEnforcementAction",
        "deletionGracePeriodInDays": 30
      },
      "rules": [
        {
          "@odata.type": "#microsoft.graph.identityGovernance.periodicAttestationRule",
          "ruleType": "periodicAttestation",
          "isEnabled": true,
          "attestationIntervalInDays": 90
        }
      ]
    }
  ]
}
```
