<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-adminwindowsupdates-post-policies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# Create policy

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new Windows update [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) object.

You can use this method with the following child object types: [driverUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatepolicy?view=graph-rest-beta), [featureUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-featureupdatepolicy?view=graph-rest-beta), and [qualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatepolicy?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Intune Administrator*, or *Windows Update Deployment Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
POST /admin/windows/updates/policies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) object.

Because **policy** is abstract, specify the concrete type in the `@odata.type` property. Supported values include `#microsoft.graph.windowsUpdates.driverUpdatePolicy`, `#microsoft.graph.windowsUpdates.featureUpdatePolicy`, and `#microsoft.graph.windowsUpdates.qualityUpdatePolicy`.

You can specify the following properties when you create a **policy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalRules | [microsoft.graph.windowsUpdates.approvalRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-approvalrule?view=graph-rest-beta) collection | The approved rule of the policy that determines which published content matches the rule on an ongoing basis. Required. |
| description | String | The policy description. The maximum length is 1,500 characters. Required. |
| displayName | String | The policy display name. The maximum length is 200 characters. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows how to create a driver and firmware update policy.

```http
POST https://graph.microsoft.com/beta/admin/windows/updates/policies
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdatePolicy",
  "displayName": "Contoso driver policy",
  "description": "Driver and firmware updates for managed devices",
  "approvalRules": [
    {
      "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdateApprovalRule",
      "deferralInDays": 7
    }
  ]
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdatePolicy",
  "approvalRules": [
    {
      "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdateApprovalRule",
      "deferralInDays": 7
    }
  ],
  "createdDateTime": "2026-09-28T10:00:00Z",
  "description": "Driver and firmware updates for managed devices",
  "displayName": "Contoso driver policy",
  "id": "11111111-1111-4111-8111-111111111111",
  "lastModifiedDateTime": "2026-09-28T10:00:00Z"
}
```
