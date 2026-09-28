<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddeviceoverview-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update managedDeviceOverview

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [managedDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceoverview?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementManagedDevices.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementManagedDevices.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/managedDeviceOverview
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [managedDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceoverview?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [managedDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceoverview?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the summary |
| enrolledDeviceCount | Int32 | Total enrolled device count. Does not include PC devices managed via Intune PC Agent |
| mdmEnrolledCount | Int32 | The number of devices enrolled in MDM |
| dualEnrolledDeviceCount | Int32 | The number of devices enrolled in both MDM and EAS |
| deviceOperatingSystemSummary | [deviceOperatingSystemSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceoperatingsystemsummary?view=graph-rest-1.0) | Device operating system summary. |
| deviceExchangeAccessStateSummary | [deviceExchangeAccessStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceexchangeaccessstatesummary?view=graph-rest-1.0) | Distribution of Exchange Access State in Intune |

## Response

If successful, this method returns a `200 OK` response code and an updated [managedDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceoverview?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceManagement/managedDeviceOverview
Content-type: application/json
Content-length: 900

{
  "@odata.type": "#microsoft.graph.managedDeviceOverview",
  "enrolledDeviceCount": 3,
  "mdmEnrolledCount": 0,
  "dualEnrolledDeviceCount": 7,
  "deviceOperatingSystemSummary": {
    "@odata.type": "microsoft.graph.deviceOperatingSystemSummary",
    "androidCount": 12,
    "iosCount": 8,
    "macOSCount": 10,
    "windowsMobileCount": 2,
    "windowsCount": 12,
    "unknownCount": 12,
    "androidDedicatedCount": 5,
    "androidDeviceAdminCount": 7,
    "androidFullyManagedCount": 8,
    "androidWorkProfileCount": 7,
    "androidCorporateWorkProfileCount": 0,
    "configMgrDeviceCount": 4
  },
  "deviceExchangeAccessStateSummary": {
    "@odata.type": "microsoft.graph.deviceExchangeAccessStateSummary",
    "allowedDeviceCount": 2,
    "blockedDeviceCount": 2,
    "quarantinedDeviceCount": 6,
    "unknownDeviceCount": 2,
    "unavailableDeviceCount": 6
  }
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 949

{
  "@odata.type": "#microsoft.graph.managedDeviceOverview",
  "id": "42a91653-1653-42a9-5316-a9425316a942",
  "enrolledDeviceCount": 3,
  "mdmEnrolledCount": 0,
  "dualEnrolledDeviceCount": 7,
  "deviceOperatingSystemSummary": {
    "@odata.type": "microsoft.graph.deviceOperatingSystemSummary",
    "androidCount": 12,
    "iosCount": 8,
    "macOSCount": 10,
    "windowsMobileCount": 2,
    "windowsCount": 12,
    "unknownCount": 12,
    "androidDedicatedCount": 5,
    "androidDeviceAdminCount": 7,
    "androidFullyManagedCount": 8,
    "androidWorkProfileCount": 7,
    "androidCorporateWorkProfileCount": 0,
    "configMgrDeviceCount": 4
  },
  "deviceExchangeAccessStateSummary": {
    "@odata.type": "microsoft.graph.deviceExchangeAccessStateSummary",
    "allowedDeviceCount": 2,
    "blockedDeviceCount": 2,
    "quarantinedDeviceCount": 6,
    "unknownDeviceCount": 2,
    "unavailableDeviceCount": 6
  }
}
```
