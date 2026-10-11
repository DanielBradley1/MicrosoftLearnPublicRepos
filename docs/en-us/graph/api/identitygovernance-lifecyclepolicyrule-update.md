<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicyrule-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# Update lifecyclePolicyRule

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-AgentId.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-AgentId.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /identityGovernance/lifecycleWorkflows/lifecyclePolicies/{lifecyclePolicyId}/rules/{lifecyclePolicyRuleId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

You must specify the `@odata.type` property when updating a [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) object. For example, to update a [periodicAttestationRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-periodicattestationrule?view=graph-rest-beta) object, set `@odata.type` to `#microsoft.graph.identityGovernance.periodicAttestationRule`.

| Property | Type | Description |
| :--- | :--- | :--- |
| attestationIntervalInDays | Int32 | The number of days between required attestations. Applies to `periodicAttestationRule`. |
| isEnabled | Boolean | Indicates whether the rule is enabled and evaluated. |
| lastActivityThresholdInDays | Int32 | The number of days of inactivity after which the identity is considered noncompliant. Applies to `inactivityRule`. |
| minimumSponsorCount | Int32 | The minimum number of sponsors an identity must have. Applies to `sponsorPresenceRule`. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/lifecyclePolicies/ba9191ab-e88f-4278-942c-4dcc6a4f05b1/rules/6f3b8c1a-2d4e-4f6a-8b0c-1e2f3a4b5c6d
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.identityGovernance.periodicAttestationRule",
  "isEnabled": false,
  "attestationIntervalInDays": 120
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
