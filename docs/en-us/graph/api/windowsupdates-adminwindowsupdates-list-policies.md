<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-adminwindowsupdates-list-policies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# List policies

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) objects and their properties.

You can use this method with the following child object types: [driverUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatepolicy?view=graph-rest-beta), [featureUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-featureupdatepolicy?view=graph-rest-beta), and [qualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatepolicy?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Intune Administrator*, or *Windows Update Deployment Administrator* are the least privileged roles supported for this operation.

## HTTP request

To get all policy objects or only policies of a specific derived type:

```http
GET /admin/windows/updates/policies
GET /admin/windows/updates/policies/microsoft.graph.windowsUpdates.driverUpdatePolicy
GET /admin/windows/updates/policies/microsoft.graph.windowsUpdates.featureUpdatePolicy
GET /admin/windows/updates/policies/microsoft.graph.windowsUpdates.qualityUpdatePolicy
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$count`, and `$top` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows how to get a list that contains each supported policy type.

```http
GET https://graph.microsoft.com/beta/admin/windows/updates/policies
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/admin/windows/updates/$metadata#policies",
  "value": [
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
    },
    {
      "@odata.type": "#microsoft.graph.windowsUpdates.featureUpdatePolicy",
      "approvalRules": [],
      "createdDateTime": "2026-09-28T10:05:00Z",
      "description": "Administrator-approved Windows feature updates",
      "displayName": "Contoso feature policy",
      "id": "22222222-2222-4222-8222-222222222222",
      "lastModifiedDateTime": "2026-09-28T10:05:00Z"
    },
    {
      "@odata.type": "#microsoft.graph.windowsUpdates.qualityUpdatePolicy",
      "approvalRules": [
        {
          "@odata.type": "#microsoft.graph.windowsUpdates.qualityUpdateApprovalRule",
          "cadence": "monthly",
          "classification": "security",
          "deferralInDays": 2
        }
      ],
      "createdDateTime": "2026-09-28T10:10:00Z",
      "description": "Monthly quality updates for production devices",
      "displayName": "Contoso quality policy",
      "id": "33333333-3333-4333-8333-333333333333",
      "lastModifiedDateTime": "2026-09-28T10:10:00Z"
    }
  ]
}
```
