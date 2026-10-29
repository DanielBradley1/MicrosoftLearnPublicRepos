<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-driverupdatedevicestatus-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# Get driver update device status

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a [driverUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatedevicestatus?view=graph-rest-beta) resource for a driver or firmware update.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |

## HTTP request

```http
GET /admin/windows/updates/data/drivers/{driverUpdateReportId}/deviceStatuses/{driverUpdateDeviceStatusId}
```

## Optional query parameters

This method supports the `$select` OData query parameter. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.windowsUpdates.driverUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatedevicestatus?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/admin/windows/updates/data/drivers/0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef/deviceStatuses/0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef_66666666-6666-4666-8666-666666666666_11111111-1111-4111-8111-111111111111_22222222-2222-4222-8222-222222222222
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdateDeviceStatus",
  "id": "0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef_66666666-6666-4666-8666-666666666666_11111111-1111-4111-8111-111111111111_22222222-2222-4222-8222-222222222222",
  "aadDeviceId": "66666666-6666-4666-8666-666666666666",
  "policyId": "11111111-1111-4111-8111-111111111111",
  "ringId": "22222222-2222-4222-8222-222222222222",
  "policyName": "Contoso driver policy",
  "ringName": "Broad deployment ring",
  "deviceName": "Contoso-Laptop-01",
  "clientState": "installed",
  "clientSubstate": "updateInstalled",
  "serviceState": "offering",
  "serviceSubstate": "offerReady",
  "lastEventDateTime": "2026-10-01T18:30:00Z"
}
```
