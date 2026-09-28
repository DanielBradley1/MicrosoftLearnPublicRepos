<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# List userExperienceAnalyticsBatteryHealthDevicePerformances

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

List properties and relationships of the [userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta) objects.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementManagedDevices.Read.All, DeviceManagementManagedDevices.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementManagedDevices.Read.All, DeviceManagementManagedDevices.ReadWrite.All |

## HTTP Request

```http
GET /deviceManagement/userExperienceAnalyticsBatteryHealthDevicePerformance
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta) objects in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/deviceManagement/userExperienceAnalyticsBatteryHealthDevicePerformance
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1066

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.userExperienceAnalyticsBatteryHealthDevicePerformance",
      "id": "c8b9e0fd-e0fd-c8b9-fde0-b9c8fde0b9c8",
      "deviceId": "Device Id value",
      "deviceName": "Device Name value",
      "model": "Model value",
      "manufacturer": "Manufacturer value",
      "deviceModelName": "Device Model Name value",
      "deviceManufacturerName": "Device Manufacturer Name value",
      "maxCapacityPercentage": 5,
      "estimatedRuntimeInMinutes": 9,
      "batteryAgeInDays": 0,
      "fullBatteryDrainCount": 5,
      "deviceBatteryCount": 2,
      "deviceBatteriesDetails": [
        {
          "@odata.type": "microsoft.graph.userExperienceAnalyticsDeviceBatteryDetail",
          "batteryId": "Battery Id value",
          "maxCapacityPercentage": 5,
          "fullBatteryDrainCount": 5
        }
      ],
      "deviceBatteryTags": [
        "Device Battery Tags value"
      ],
      "deviceBatteryHealthScore": 8,
      "healthStatus": "insufficientData"
    }
  ]
}
```
