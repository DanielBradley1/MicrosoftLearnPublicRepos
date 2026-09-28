<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicestate-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update deviceManagementIntentDeviceState

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) object.

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
PATCH /deviceManagement/intents/{deviceManagementIntentId}/deviceStates/{deviceManagementIntentDeviceStateId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID |
| userPrincipalName | String | The user principal name that is being reported on a device |
| userName | String | The user name that is being reported on a device |
| deviceDisplayName | String | Device name that is being reported |
| lastReportedDateTime | DateTimeOffset | Last modified date time of an intent report |
| state | [complianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-compliancestatus?view=graph-rest-beta) | Device state for an intent. Possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`. |
| deviceId | String | Device id that is being reported |

## Response

If successful, this method returns a `200 OK` response code and an updated [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/intents/{deviceManagementIntentId}/deviceStates/{deviceManagementIntentDeviceStateId}
Content-type: application/json
Content-length: 342

{
  "@odata.type": "#microsoft.graph.deviceManagementIntentDeviceState",
  "userPrincipalName": "User Principal Name value",
  "userName": "User Name value",
  "deviceDisplayName": "Device Display Name value",
  "lastReportedDateTime": "2017-01-01T00:00:17.7769392-08:00",
  "state": "notApplicable",
  "deviceId": "Device Id value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 391

{
  "@odata.type": "#microsoft.graph.deviceManagementIntentDeviceState",
  "id": "8db75881-5881-8db7-8158-b78d8158b78d",
  "userPrincipalName": "User Principal Name value",
  "userName": "User Name value",
  "deviceDisplayName": "Device Display Name value",
  "lastReportedDateTime": "2017-01-01T00:00:17.7769392-08:00",
  "state": "notApplicable",
  "deviceId": "Device Id value"
}
```
