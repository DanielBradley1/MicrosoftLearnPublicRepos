<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-tenantsetting-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# Get tenant settings

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the [tenantSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-tenantsetting?view=graph-rest-beta) singleton for the current tenant. When no settings have been saved, this operation returns the default settings, with **areDataProcessorServiceForWindowsFeaturesEnabled** set to `false`.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |

## HTTP request

```http
GET /admin/windows/updates/tenantSettings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.windowsUpdates.tenantSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-tenantsetting?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/admin/windows/updates/tenantSettings
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.tenantSetting",
  "areDataProcessorServiceForWindowsFeaturesEnabled": false
}
```
