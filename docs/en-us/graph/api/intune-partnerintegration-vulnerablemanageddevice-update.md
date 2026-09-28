<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-vulnerablemanageddevice-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update vulnerableManagedDevice

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
PATCH ** Entity URI for microsoft.management.services.api.vulnerableManagedDevice not found
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The entity key, and AAD device ID. |
| managedDeviceId | String | The Intune managed device ID. |
| displayName | String | The device name. |
| lastSyncDateTime | DateTimeOffset | The last sync date. |

## Response

If successful, this method returns a `200 OK` response code and an updated [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta** Entity URI for microsoft.management.services.api.vulnerableManagedDevice not found
Content-type: application/json
Content-length: 214

{
  "@odata.type": "#microsoft.graph.vulnerableManagedDevice",
  "managedDeviceId": "Managed Device Id value",
  "displayName": "Display Name value",
  "lastSyncDateTime": "2017-01-01T00:02:49.3205976-08:00"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 263

{
  "@odata.type": "#microsoft.graph.vulnerableManagedDevice",
  "id": "e59891d4-91d4-e598-d491-98e5d49198e5",
  "managedDeviceId": "Managed Device Id value",
  "displayName": "Display Name value",
  "lastSyncDateTime": "2017-01-01T00:02:49.3205976-08:00"
}
```
