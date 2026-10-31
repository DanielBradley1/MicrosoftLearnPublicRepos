<!-- Source: https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicyplan-post-rules?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# Create conditionalAccessPolicyRule

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [conditionalAccessPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.ConditionalAccess | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.ConditionalAccess | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Conditional Access Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /identity/conditionalAccess/plans/{conditionalAccessPolicyPlanId}/rules
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [conditionalAccessPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta) object.

You can specify the following properties when creating a **conditionalAccessPolicyRule**.

| Property | Type | Description |
| :--- | :--- | :--- |
| conditions | [conditionalAccessConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessconditionset?view=graph-rest-beta) | The conditions specific to the rule. During evaluation, these conditions are combined with the parent plan's **sharedConditions** property to determine the rule's effective targeting. Optional. |
| controls | [conditionalAccessPolicyRuleControls](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrulecontrols?view=graph-rest-beta) | The grant and session controls enforced when the rule's effective conditions are met. Required. |
| description | String | A free-text description of the rule's purpose. Optional. |
| displayName | String | The administrator-defined display name for the rule. Required. |
| state | [conditionalAccessPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#conditionalaccesspolicystate-values) | The state of the rule. The possible values are: `enabled`, `disabled`, `enabledForReportingButNotEnforced`. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [conditionalAccessPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/identity/conditionalAccess/plans/d1e2f3a4-b5c6-7d8e-9f0a-1b2c3d4e5f6a/rules
Content-Type: application/json

{
  "displayName": "Require compliant Windows devices",
  "description": "Requires Windows devices to be compliant.",
  "state": "enabled",
  "conditions": {
    "users": {
      "includeUsers": [
        "All"
      ]
    },
    "applications": {
      "includeApplications": [
        "All"
      ]
    }
  },
  "controls": {
    "grantControls": {
      "operator": "OR",
      "builtInControls": [
        "compliantDevice"
      ]
    }
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
  "@odata.type": "#microsoft.graph.conditionalAccessPolicyRule",
  "id": "d1e2f3a4-b5c6-7d8e-9f0a-100000000001",
  "displayName": "Require compliant Windows devices",
  "description": "Requires Windows devices to be compliant.",
  "state": "enabled",
  "conditions": {
    "@odata.type": "microsoft.graph.conditionalAccessConditionSet",
    "users": {
      "includeUsers": [
        "All"
      ]
    },
    "applications": {
      "includeApplications": [
        "All"
      ]
    }
  },
  "controls": {
    "@odata.type": "microsoft.graph.conditionalAccessPolicyRuleControls",
    "grantControls": {
      "operator": "OR",
      "builtInControls": [
        "compliantDevice"
      ]
    }
  }
}
```
