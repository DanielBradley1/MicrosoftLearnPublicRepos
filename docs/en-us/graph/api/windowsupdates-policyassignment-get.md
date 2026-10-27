<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-policyassignment-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# Get policy assignment

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a [policyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyassignment?view=graph-rest-beta) resource that associates a Windows Autopatch policy with a device.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |

## HTTP request

```http
GET /admin/windows/updates/data/policyAssignments/{policyAssignmentId}
```

## Optional query parameters

This method supports the `$expand` and `$select` OData query parameters. For `$expand`, only the `deviceProfile` relationship is supported. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.windowsUpdates.policyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyassignment?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/admin/windows/updates/data/policyAssignments/bc11d699-c171-bde8-e0d6-33a182d12841
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.policyAssignment",
  "id": "bc11d699-c171-bde8-e0d6-33a182d12841",
  "policyId": "11111111-1111-4111-8111-111111111111",
  "policyName": "Contoso driver policy",
  "azureAdDeviceId": "66666666-6666-4666-8666-666666666666"
}
```
