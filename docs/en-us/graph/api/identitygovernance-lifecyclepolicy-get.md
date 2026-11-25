<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Get lifecyclePolicy

Namespace: microsoft.graph.identityGovernance

Read the properties and relationships of [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) object.

You can also retrieve a soft-deleted policy from the lifecycle workflows deleted items container.

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
GET /identityGovernance/lifecycleWorkflows/lifecyclePolicies/{lifecyclePolicyId}
GET /identityGovernance/lifecycleWorkflows/deletedItems/lifecyclePolicies/{lifecyclePolicyId}
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

If successful, this method returns a `200 OK` response code and a [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/lifecyclePolicies/ba9191ab-e88f-4278-942c-4dcc6a4f05b1
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
      "isEnabled": true,
      "attestationIntervalInDays": 90
    },
    {
      "@odata.type": "#microsoft.graph.identityGovernance.sponsorPresenceRule",
      "isEnabled": true,
      "minimumSponsorCount": 1
    }
  ],
  "notificationSchedule": {
    "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings",
    "additionalFallbackRecipients": ["admins@contoso.com"],
    "offsetsAfterNonComplianceInDays": [14, 7, 1]
  }
}
```
