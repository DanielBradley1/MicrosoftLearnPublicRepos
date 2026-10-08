<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicypriorityconfiguration-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# Get lifecyclePolicyPriorityConfiguration

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the properties and relationships of a [microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-beta) object. The configuration is keyed by subject type and returns the evaluation order of lifecycle policies for that subject type.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-AgentId.Read.All | LifecyclePolicies-AgentId.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-AgentId.Read.All | LifecyclePolicies-AgentId.ReadWrite.All |

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/lifecyclePolicyPriorityConfigurations/{subjectType}
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

If successful, this method returns a `200 OK` response code and a [microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/lifecyclePolicyPriorityConfigurations/agentIdentity
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration",
  "id": "agentIdentity",
  "subjectType": "agentIdentity",
  "orderedPolicyIds": [
    "ba9191ab-e88f-4278-942c-4dcc6a4f05b1",
    "f360e310-e2c9-4bb3-a3ca-791d3c0b6548"
  ]
}
```
