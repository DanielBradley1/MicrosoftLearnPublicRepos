<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-restrictedappsviolation-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create restrictedAppsViolation

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta) object.

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
POST /deviceManagement/deviceConfigurationRestrictedAppsViolations
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the restrictedAppsViolation object.

The following table shows the properties that are required when you create the restrictedAppsViolation.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the object. Composed from accountId, deviceId, policyId and userId |
| userId | String | User unique identifier, must be Guid |
| userName | String | User name |
| managedDeviceId | String | Managed device unique identifier, must be Guid |
| deviceName | String | Device name |
| deviceConfigurationId | String | Device configuration profile unique identifier, must be Guid |
| deviceConfigurationName | String | Device configuration profile name |
| platformType | [policyPlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-policyplatformtype?view=graph-rest-beta) | Platform type. Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `windows10XProfile`, `androidAOSP`, `linux`, `all`. |
| restrictedAppsState | [restrictedAppsState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsstate?view=graph-rest-beta) | Restricted apps state. Possible values are: `prohibitedApps`, `notApprovedApps`. |
| restrictedApps | [managedDeviceReportedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicereportedapp?view=graph-rest-beta) collection | List of violated restricted apps |

## Response

If successful, this method returns a `201 Created` response code and a [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/deviceConfigurationRestrictedAppsViolations
Content-type: application/json
Content-length: 564

{
  "@odata.type": "#microsoft.graph.restrictedAppsViolation",
  "userId": "User Id value",
  "userName": "User Name value",
  "managedDeviceId": "Managed Device Id value",
  "deviceName": "Device Name value",
  "deviceConfigurationId": "Device Configuration Id value",
  "deviceConfigurationName": "Device Configuration Name value",
  "platformType": "androidForWork",
  "restrictedAppsState": "notApprovedApps",
  "restrictedApps": [
    {
      "@odata.type": "microsoft.graph.managedDeviceReportedApp",
      "appId": "App Id value"
    }
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 613

{
  "@odata.type": "#microsoft.graph.restrictedAppsViolation",
  "id": "53f99903-9903-53f9-0399-f9530399f953",
  "userId": "User Id value",
  "userName": "User Name value",
  "managedDeviceId": "Managed Device Id value",
  "deviceName": "Device Name value",
  "deviceConfigurationId": "Device Configuration Id value",
  "deviceConfigurationName": "Device Configuration Name value",
  "platformType": "androidForWork",
  "restrictedAppsState": "notApprovedApps",
  "restrictedApps": [
    {
      "@odata.type": "microsoft.graph.managedDeviceReportedApp",
      "appId": "App Id value"
    }
  ]
}
```
