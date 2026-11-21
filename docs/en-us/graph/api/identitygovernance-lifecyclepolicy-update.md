<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Update lifecyclePolicy

Namespace: microsoft.graph.identityGovernance

Update the properties of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) object.

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
PATCH /identityGovernance/lifecycleWorkflows/lifecyclePolicies/{lifecyclePolicyId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

You must specify the `@odata.type` property when updating a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) object. For example, to update an [agentIdentityLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecyclepolicy?view=graph-rest-1.0) object, set `@odata.type` to `#microsoft.graph.identityGovernance.agentIdentityLifecyclePolicy`.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description for the policy. |
| displayName | String | The display name for the policy. |
| enforcementAction | [microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-1.0) | The action taken against identities that fail to meet the policy's rules. This polymorphic type has the derived types `disableOnlyEnforcementAction`, `deleteOnlyEnforcementAction`, and `disableThenDeleteEnforcementAction`. |
| isEnabled | Boolean | Indicates whether the policy is enabled and evaluated. |
| gracePeriodInDays | Int32 | The policy-level grace period before enforcement. A rule-level value overrides this value for that rule. |
| notificationSchedule | [microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicynotificationsettings?view=graph-rest-1.0) | The notification schedule that determines when reminders are sent before enforcement. |
| scope | [microsoft.graph.subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) | The set of identities the policy applies to. |

## Response

If successful, this method returns a `204 No Content` response code.

### Errors

This method returns a `400 Bad Request` response code with the `lifecyclePolicyRulesLimitExceeded` error code if the update would exceed the maximum of 10 rules per policy, or the `lifecyclePolicyExcludedGroupsLimitExceeded` error code if the exclusion scope would exceed the maximum of 10 excluded groups per policy.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/lifecyclePolicies/ba9191ab-e88f-4278-942c-4dcc6a4f05b1
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.identityGovernance.agentIdentityLifecyclePolicy",
  "displayName": "Agent attestation with sponsor requirement (v2)",
  "isEnabled": false,
  "enforcementAction": {
    "@odata.type": "#microsoft.graph.identityGovernance.disableThenDeleteEnforcementAction",
    "deletionGracePeriodInDays": 45
  }
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
