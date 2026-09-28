<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-executeaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# executeAction action

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementManagedDevices.PrivilegedOperations.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementManagedDevices.PrivilegedOperations.All |

## HTTP Request

```http
POST /deviceManagement/managedDevices/executeAction
POST /deviceManagement/comanagedDevices/executeAction
POST /deviceManagement/deviceManagementScripts/{deviceManagementScriptId}/deviceRunStates/{deviceManagementScriptDeviceStateId}/managedDevice/users/{userId}/managedDevices/executeAction
POST /deviceManagement/deviceManagementScripts/{deviceManagementScriptId}/deviceRunStates/{deviceManagementScriptDeviceStateId}/managedDevice/detectedApps/{detectedAppId}/managedDevices/executeAction
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Property | Type | Description |
| :--- | :--- | :--- |
| actionName | [managedDeviceRemoteAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceremoteaction?view=graph-rest-beta) |  |
| keepEnrollmentData | Boolean |  |
| keepUserData | Boolean |  |
| persistEsimDataPlan | Boolean |  |
| deviceIds | String collection |  |
| notificationTitle | String |  |
| notificationBody | String |  |
| deviceName | String |  |
| carrierUrl | String |  |
| deprovisionReason | String |  |
| organizationalUnitPath | String |  |

## Response

If successful, this action returns a `200 OK` response code and a [bulkManagedDeviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-bulkmanageddeviceactionresult?view=graph-rest-beta) in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/managedDevices/executeAction

Content-type: application/json
Content-length: 473

{
  "actionName": "delete",
  "keepEnrollmentData": true,
  "keepUserData": true,
  "persistEsimDataPlan": true,
  "deviceIds": [
    "Device Ids value"
  ],
  "notificationTitle": "Notification Title value",
  "notificationBody": "Notification Body value",
  "deviceName": "Device Name value",
  "carrierUrl": "https://example.com/carrierUrl/",
  "deprovisionReason": "Deprovision Reason value",
  "organizationalUnitPath": "Organizational Unit Path value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 385

{
  "value": {
    "@odata.type": "microsoft.graph.bulkManagedDeviceActionResult",
    "successfulDeviceIds": [
      "Successful Device Ids value"
    ],
    "failedDeviceIds": [
      "Failed Device Ids value"
    ],
    "notFoundDeviceIds": [
      "Not Found Device Ids value"
    ],
    "notSupportedDeviceIds": [
      "Not Supported Device Ids value"
    ]
  }
}
```
