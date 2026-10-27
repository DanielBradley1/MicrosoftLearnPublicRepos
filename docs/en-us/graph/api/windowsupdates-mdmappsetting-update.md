<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-mdmappsetting-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# Update MDM app setting

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update an [mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) resource within the current tenant. The **mdmAppId** is identified by the request URL and can't be changed by this operation.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /admin/windows/updates/tenantSettings/mdmAppSettings/{mdmAppId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| isHotpatchEnabled | Boolean | Whether hotpatch is enabled for this MDM application. Specify this property to change its value. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.windowsUpdates.mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/admin/windows/updates/tenantSettings/mdmAppSettings/6e8fb67d-ac92-5b14-8d6d-3299f92da00c
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.mdmAppSetting",
  "isHotpatchEnabled": false
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.mdmAppSetting",
  "mdmAppId": "6e8fb67d-ac92-5b14-8d6d-3299f92da00c",
  "isHotpatchEnabled": false
}
```
