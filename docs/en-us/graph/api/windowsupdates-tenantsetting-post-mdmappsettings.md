<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-tenantsetting-post-mdmappsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# Create MDM app setting

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create an [mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) resource for an MDM application in the current tenant.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.ReadWrite.All | Not available. |

## HTTP request

```http
POST /admin/windows/updates/tenantSettings/mdmAppSettings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.windowsUpdates.mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) object.

You can specify the following properties when creating a **mdmAppSetting**.

| Property | Type | Description |
| :--- | :--- | :--- |
| isHotpatchEnabled | Boolean | Whether hotpatch is enabled for this MDM application. The default is `true`. Required. |
| mdmAppId | String | The unique identifier of the MDM application. Must be a nonempty GUID-formatted string. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.windowsUpdates.mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/admin/windows/updates/tenantSettings/mdmAppSettings
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.mdmAppSetting",
  "mdmAppId": "6e8fb67d-ac92-5b14-8d6d-3299f92da00c",
  "isHotpatchEnabled": true
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.mdmAppSetting",
  "mdmAppId": "6e8fb67d-ac92-5b14-8d6d-3299f92da00c",
  "isHotpatchEnabled": true
}
```
