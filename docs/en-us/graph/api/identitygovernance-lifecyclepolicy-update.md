<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# Update lifecyclePolicy

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-AgentId.ReadWrite.All | LifecyclePolicies-Guests.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-AgentId.ReadWrite.All | LifecyclePolicies-Guests.ReadWrite.All |

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

You must specify the `@odata.type` property when updating a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) object. For example, to update an [agentIdentityLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecyclepolicy?view=graph-rest-beta) object, set `@odata.type` to `#microsoft.graph.identityGovernance.agentIdentityLifecyclePolicy`.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description for the policy. |
| displayName | String | The display name for the policy. |
| enforcementAction | [microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-beta) | The action taken against identities that fail to meet the policy's rules. This polymorphic type has the derived types `disableOnlyEnforcementAction`, `deleteOnlyEnforcementAction`, and `disableThenDeleteEnforcementAction`. |
| isEnabled | Boolean | Indicates whether the policy is enabled and evaluated. |
| notificationSchedule | [microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicynotificationsettings?view=graph-rest-beta) | The notification schedule that determines when reminders are sent before enforcement. |
| scope | [microsoft.graph.subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-beta) | The set of identities the policy applies to. |

## Response

If successful, this method returns a `204 No Content` response code.

### Errors

This method returns a `400 Bad Request` response code with the `lifecyclePolicyRulesLimitExceeded` error code if the update would exceed the maximum of 10 rules per policy, or the `lifecyclePolicyExcludedGroupsLimitExceeded` error code if the exclusion scope would exceed the maximum of 10 excluded groups per policy.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/lifecyclePolicies/ba9191ab-e88f-4278-942c-4dcc6a4f05b1
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
