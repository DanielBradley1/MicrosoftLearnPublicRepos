<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsworkfromanywherehardwarereadinessmetric-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Get userExperienceAnalyticsWorkFromAnywhereHardwareReadinessMetric

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Read properties and relationships of the [userExperienceAnalyticsWorkFromAnywhereHardwareReadinessMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywherehardwarereadinessmetric?view=graph-rest-1.0) object.

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
GET /deviceManagement/userExperienceAnalyticsWorkFromAnywhereHardwareReadinessMetric
```

## Optional query parameters

This method supports the [OData Query Parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and [userExperienceAnalyticsWorkFromAnywhereHardwareReadinessMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywherehardwarereadinessmetric?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/v1.0/deviceManagement/userExperienceAnalyticsWorkFromAnywhereHardwareReadinessMetric
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 720

{
  "value": {
    "@odata.type": "#microsoft.graph.userExperienceAnalyticsWorkFromAnywhereHardwareReadinessMetric",
    "id": "6df21a06-1a06-6df2-061a-f26d061af26d",
    "totalDeviceCount": 0,
    "upgradeEligibleDeviceCount": 10,
    "ramCheckFailedPercentage": 8.0,
    "storageCheckFailedPercentage": 9.3333333333333339,
    "processorCoreCountCheckFailedPercentage": 13.0,
    "processorSpeedCheckFailedPercentage": 11.666666666666666,
    "tpmCheckFailedPercentage": 8.0,
    "secureBootCheckFailedPercentage": 10.333333333333334,
    "processorFamilyCheckFailedPercentage": 12.0,
    "processor64BitCheckFailedPercentage": 11.666666666666666,
    "osCheckFailedPercentage": 7.666666666666667
  }
}
```
