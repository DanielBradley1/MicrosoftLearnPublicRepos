<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-shared-windowsupdatestate-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Update windowsUpdateState

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

```
    ## Permissions
```

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from most to least privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) |  |
| **Device configuration** | DeviceManagementConfiguration.ReadWrite.All |
| **Software Update** | DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application |  |
| **Device configuration** | DeviceManagementConfiguration.ReadWrite.All |
| **Software Update** | DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.windowsUpdateForBusinessConfiguration/deviceUpdateStates/{windowsUpdateStateId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | This is Id of the entity. |
| deviceId | String | The id of the device. |
| userId | String | The id of the user. |
| deviceDisplayName | String | Device display name. |
| userPrincipalName | String | User principal name. |
| status | [windowsUpdateStatus](https://learn.microsoft.com/en-us/graph/resources/intune-shared-windowsupdatestatus.md?view=graph-rest-beta) | Windows udpate status. The possible values are: `upToDate`, `pendingInstallation`, `pendingReboot`, `failed`. |
| qualityUpdateVersion | String | The Quality Update Version of the device. |
| featureUpdateVersion | String | The current feature update version of the device. |
| lastScanDateTime | DateTimeOffset | The date time that the Windows Update Agent did a successful scan. |
| lastSyncDateTime | DateTimeOffset | Last date time that the device sync with with Microsoft Intune. |

## Response

If successful, this method returns a `200 OK` response code and an updated [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.windowsUpdateForBusinessConfiguration/deviceUpdateStates/{windowsUpdateStateId}
Content-type: application/json
Content-length: 504

{
  "@odata.type": "#microsoft.graph.windowsUpdateState",
  "deviceId": "Device Id value",
  "userId": "User Id value",
  "deviceDisplayName": "Device Display Name value",
  "userPrincipalName": "User Principal Name value",
  "status": "pendingInstallation",
  "qualityUpdateVersion": "Quality Update Version value",
  "featureUpdateVersion": "Feature Update Version value",
  "lastScanDateTime": "2016-12-31T23:59:18.0955018-08:00",
  "lastSyncDateTime": "2017-01-01T00:02:49.3205976-08:00"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 553

{
  "@odata.type": "#microsoft.graph.windowsUpdateState",
  "id": "3d92af00-af00-3d92-00af-923d00af923d",
  "deviceId": "Device Id value",
  "userId": "User Id value",
  "deviceDisplayName": "Device Display Name value",
  "userPrincipalName": "User Principal Name value",
  "status": "pendingInstallation",
  "qualityUpdateVersion": "Quality Update Version value",
  "featureUpdateVersion": "Feature Update Version value",
  "lastScanDateTime": "2016-12-31T23:59:18.0955018-08:00",
  "lastSyncDateTime": "2017-01-01T00:02:49.3205976-08:00"
}
```
