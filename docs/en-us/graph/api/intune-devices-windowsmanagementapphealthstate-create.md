<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanagementapphealthstate-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create windowsManagementAppHealthState

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementManagedDevices.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementManagedDevices.ReadWrite.All |

## HTTP Request

```http
POST /deviceAppManagement/windowsManagementApp/healthStates
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the windowsManagementAppHealthState object.

The following table shows the properties that are required when you create the windowsManagementAppHealthState.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the Windows management app health state. This property is read-only. |
| healthState | [healthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-healthstate?view=graph-rest-beta) | Windows management app health state. Possible values are: `unknown`, `healthy`, `unhealthy`. |
| installedVersion | String | Windows management app installed version. |
| lastCheckInDateTime | DateTimeOffset | Windows management app last check-in time. |
| deviceName | String | Name of the device on which Windows management app is installed. |
| deviceOSVersion | String | Windows 10 OS version of the device on which Windows management app is installed. |

## Response

If successful, this method returns a `201 Created` response code and a [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceAppManagement/windowsManagementApp/healthStates
Content-type: application/json
Content-length: 300

{
  "@odata.type": "#microsoft.graph.windowsManagementAppHealthState",
  "healthState": "healthy",
  "installedVersion": "Installed Version value",
  "lastCheckInDateTime": "2016-12-31T23:59:56.413532-08:00",
  "deviceName": "Device Name value",
  "deviceOSVersion": "Device OSVersion value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 349

{
  "@odata.type": "#microsoft.graph.windowsManagementAppHealthState",
  "id": "5c7e50fb-50fb-5c7e-fb50-7e5cfb507e5c",
  "healthState": "healthy",
  "installedVersion": "Installed Version value",
  "lastCheckInDateTime": "2016-12-31T23:59:56.413532-08:00",
  "deviceName": "Device Name value",
  "deviceOSVersion": "Device OSVersion value"
}
```
