<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-applicablecatalog-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# Get applicable catalog

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get an [applicableCatalog](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalog?view=graph-rest-beta) resource for a Windows Autopatch policy.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |

## HTTP request

```http
GET /admin/windows/updates/policies/{policyId}/applicableCatalogs/{applicableCatalogId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.windowsUpdates.applicableCatalog](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalog?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/admin/windows/updates/policies/11111111-1111-4111-8111-111111111111/applicableCatalogs/0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.applicableCatalog",
  "id": "0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef",
  "deviceCount": 12,
  "hasRecommendedDevice": true
}
```
