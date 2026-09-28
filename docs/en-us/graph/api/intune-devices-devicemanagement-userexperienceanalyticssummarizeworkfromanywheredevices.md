<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagement-userexperienceanalyticssummarizeworkfromanywheredevices?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# userExperienceAnalyticsSummarizeWorkFromAnywhereDevices function

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

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
GET /deviceManagement/userExperienceAnalyticsSummarizeWorkFromAnywhereDevices
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [userExperienceAnalyticsWorkFromAnywhereDevicesSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevicessummary?view=graph-rest-1.0) in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/v1.0/deviceManagement/userExperienceAnalyticsSummarizeWorkFromAnywhereDevices
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1355

{
  "value": {
    "@odata.type": "microsoft.graph.userExperienceAnalyticsWorkFromAnywhereDevicesSummary",
    "autopilotDevicesSummary": {
      "@odata.type": "microsoft.graph.userExperienceAnalyticsAutopilotDevicesSummary",
      "devicesNotAutopilotRegistered": 13,
      "devicesWithoutAutopilotProfileAssigned": 6,
      "totalWindows10DevicesWithoutTenantAttached": 10
    },
    "cloudManagementDevicesSummary": {
      "@odata.type": "microsoft.graph.userExperienceAnalyticsCloudManagementDevicesSummary",
      "coManagedDeviceCount": 4,
      "intuneDeviceCount": 1,
      "tenantAttachDeviceCount": 7
    },
    "windows10DevicesSummary": {
      "@odata.type": "microsoft.graph.userExperienceAnalyticsWindows10DevicesSummary",
      "unsupportedOSversionDeviceCount": 15
    },
    "cloudIdentityDevicesSummary": {
      "@odata.type": "microsoft.graph.userExperienceAnalyticsCloudIdentityDevicesSummary",
      "deviceWithoutCloudIdentityCount": 15
    },
    "totalDevices": 12,
    "coManagedDevices": 0,
    "intuneDevices": 13,
    "tenantAttachDevices": 3,
    "windows10Devices": 0,
    "windows10DevicesWithoutTenantAttach": 3,
    "unsupportedOSversionDevices": 11,
    "devicesWithoutCloudIdentity": 11,
    "devicesNotAutopilotRegistered": 13,
    "devicesWithoutAutopilotProfileAssigned": 6
  }
}
```
