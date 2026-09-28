<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwarepassworddetail-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create hardwarePasswordDetail

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [hardwarePasswordDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepassworddetail?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/hardwarePasswordDetails
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the hardwarePasswordDetail object.

The following table shows the properties that are required when you create the hardwarePasswordDetail.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the managed device. This ID is assigned at enrollment time. This is different than the Entra device ID, this one is for the managedDevice object itself. Supports: $filter, $select, $top, $OrderBy, $skip. This property is read-only. |
| serialNumber | String | The device serial number as defined by the device manufacturer. Supports: $filter, $select, $top, $OrderBy, $skip. This property is read-only. |
| currentPassword | String | The current device's BIOS password. Supports: $filter, $select, $top, $OrderBy, $skip. This property is read-only. |
| previousPasswords | String collection | The list of all the previous device BIOS passwords. Supports: $filter, $select, $top, $skip. This property is read-only. |

## Response

If successful, this method returns a `201 Created` response code and a [hardwarePasswordDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepassworddetail?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/hardwarePasswordDetails
Content-type: application/json
Content-length: 218

{
  "@odata.type": "#microsoft.graph.hardwarePasswordDetail",
  "serialNumber": "Serial Number value",
  "currentPassword": "Current Password value",
  "previousPasswords": [
    "Previous Passwords value"
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 267

{
  "@odata.type": "#microsoft.graph.hardwarePasswordDetail",
  "id": "e3ef8349-8349-e3ef-4983-efe34983efe3",
  "serialNumber": "Serial Number value",
  "currentPassword": "Current Password value",
  "previousPasswords": [
    "Previous Passwords value"
  ]
}
```
