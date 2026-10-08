<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-restore?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicy: restore

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Restore a soft-deleted [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) object. Use this action to recover a policy that was removed with the [delete](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-delete?view=graph-rest-beta) operation and still appears in the deleted items container.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-AgentId.ReadWrite.All | LifecyclePolicies-Guests.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-AgentId.ReadWrite.All | LifecyclePolicies-Guests.ReadWrite.All |

## HTTP request

```http
POST /identityGovernance/lifecycleWorkflows/deletedItems/lifecyclePolicies/{lifecyclePolicyId}/restore
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code and a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/deletedItems/lifecyclePolicies/ba9191ab-e88f-4278-942c-4dcc6a4f05b1/restore
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.identityGovernance.agentIdentityLifecyclePolicy",
  "id": "ba9191ab-e88f-4278-942c-4dcc6a4f05b1",
  "displayName": "Agent attestation with sponsor requirement",
  "description": "Requires attestation every 90 days and at least 1 sponsor",
  "policySource": "userCreated",
  "isEnabled": true,
  "scope": null,
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
```
