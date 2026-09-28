<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsworkfromanywheredevice-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# List userExperienceAnalyticsWorkFromAnywhereDevices

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

List properties and relationships of the [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0) objects.

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
GET /deviceManagement/userExperienceAnalyticsWorkFromAnywhereMetrics/{userExperienceAnalyticsWorkFromAnywhereMetricId}/metricDevices
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0) objects in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/v1.0/deviceManagement/userExperienceAnalyticsWorkFromAnywhereMetrics/{userExperienceAnalyticsWorkFromAnywhereMetricId}/metricDevices
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1549

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.userExperienceAnalyticsWorkFromAnywhereDevice",
      "id": "83d5adfc-adfc-83d5-fcad-d583fcadd583",
      "deviceId": "Device Id value",
      "deviceName": "Device Name value",
      "serialNumber": "Serial Number value",
      "manufacturer": "Manufacturer value",
      "model": "Model value",
      "ownership": "Ownership value",
      "managedBy": "Managed By value",
      "autoPilotRegistered": true,
      "autoPilotProfileAssigned": true,
      "azureAdRegistered": true,
      "azureAdDeviceId": "Azure Ad Device Id value",
      "azureAdJoinType": "Azure Ad Join Type value",
      "osDescription": "Os Description value",
      "osVersion": "Os Version value",
      "tenantAttached": true,
      "compliancePolicySetToIntune": true,
      "otherWorkloadsSetToIntune": true,
      "isCloudManagedGatewayEnabled": true,
      "upgradeEligibility": "unknown",
      "ramCheckFailed": true,
      "storageCheckFailed": true,
      "processorCoreCountCheckFailed": true,
      "processorSpeedCheckFailed": true,
      "tpmCheckFailed": true,
      "secureBootCheckFailed": true,
      "processorFamilyCheckFailed": true,
      "processor64BitCheckFailed": true,
      "osCheckFailed": true,
      "workFromAnywhereScore": 7.0,
      "windowsScore": 4.0,
      "cloudManagementScore": 6.666666666666667,
      "cloudIdentityScore": 6.0,
      "cloudProvisioningScore": 7.333333333333333,
      "healthStatus": "insufficientData"
    }
  ]
}
```
