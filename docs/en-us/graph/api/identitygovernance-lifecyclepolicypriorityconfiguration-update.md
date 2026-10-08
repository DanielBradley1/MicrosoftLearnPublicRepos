<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicypriorityconfiguration-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# Update lifecyclePolicyPriorityConfiguration

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-beta) object to reorder the evaluation priority of lifecycle policies for a subject type.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-AgentId.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-AgentId.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /identityGovernance/lifecycleWorkflows/lifecyclePolicyPriorityConfigurations/{subjectType}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | The ETag of the lifecycle policy priority configuration. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| orderedPolicyIds | String collection | The ordered list of lifecycle policy IDs, from highest to lowest priority, for the subject type. Only the highest-priority matching policy binds to an identity. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/lifecyclePolicyPriorityConfigurations/agentIdentity
Content-Type: application/json
If-Match: W/"JzEtVGFncCc="

{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration",
  "orderedPolicyIds": [
    "f360e310-e2c9-4bb3-a3ca-791d3c0b6548",
    "ba9191ab-e88f-4278-942c-4dcc6a4f05b1"
  ]
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
