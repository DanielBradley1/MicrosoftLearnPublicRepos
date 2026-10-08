<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-post-lifecyclepolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# Create lifecyclePolicy

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) object in the [lifecycle workflows container](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflowscontainer?view=graph-rest-beta). A policy is created for a specific subject type and takes effect according to its priority order.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-AgentId.ReadWrite.All | LifecyclePolicies-Guests.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-AgentId.ReadWrite.All | LifecyclePolicies-Guests.ReadWrite.All |

## HTTP request

```http
POST /identityGovernance/lifecycleWorkflows/lifecyclePolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) object. Because **lifecyclePolicy** is an abstract type, specify the `@odata.type` of a derived type, such as `#microsoft.graph.identityGovernance.agentIdentityLifecyclePolicy`.

You can specify the following properties when creating a **lifecyclePolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description for the policy. Optional. |
| displayName | String | The display name for the policy. Required. |
| enforcementAction | [microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-beta) | The action taken against identities that fail to meet the policy's rules. This polymorphic type has the derived types `disableOnlyEnforcementAction`, `deleteOnlyEnforcementAction`, and `disableThenDeleteEnforcementAction`. Required. |
| isEnabled | Boolean | Indicates whether the policy is enabled and evaluated. Required. |
| notificationSchedule | [microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicynotificationsettings?view=graph-rest-beta) | The notification schedule that determines when reminders are sent before enforcement. Optional. |
| rules | [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) collection | The inline compliance rules evaluated with AND logic. Each rule specifies its own `@odata.type`, such as `#microsoft.graph.identityGovernance.periodicAttestationRule`. A maximum of 10 rules are allowed per policy. Optional. |
| scope | [microsoft.graph.subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-beta) | The set of identities the policy applies to. Supports scope types such as `selectedObjectsSubjectSet`, `allExcludingSpecificObjectsSubjectSet`, and `allExcludingGroupsSubjectSet`. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) object in the response body.

### Errors

This method returns a `400 Bad Request` response code with one of the following error codes when a tenant limit is exceeded:

| Error code | Description |
| :--- | :--- |
| `lifecyclePoliciesPerSubjectLimitExceeded` | A maximum of 10 lifecycle policies are allowed per subject type per tenant. |
| `lifecyclePolicyRulesLimitExceeded` | A maximum of 10 rules are allowed per lifecycle policy. |
| `lifecyclePolicyExcludedGroupsLimitExceeded` | A maximum of 10 excluded groups are allowed per lifecycle policy. |

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/lifecyclePolicies
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.identityGovernance.agentIdentityLifecyclePolicy",
  "displayName": "Agent attestation with sponsor requirement",
  "description": "Requires attestation every 90 days and at least 1 sponsor",
  "isEnabled": true,
  "enforcementAction": {
    "@odata.type": "#microsoft.graph.identityGovernance.disableThenDeleteEnforcementAction",
    "deletionGracePeriodInDays": 30
  },
  "scope": null,
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

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
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
    },
    {
      "@odata.type": "#microsoft.graph.identityGovernance.sponsorPresenceRule",
      "ruleType": "sponsorPresence",
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
