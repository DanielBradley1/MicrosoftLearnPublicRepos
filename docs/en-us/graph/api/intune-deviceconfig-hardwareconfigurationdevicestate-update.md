<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationdevicestate-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update hardwareConfigurationDeviceState

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [hardwareConfigurationDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationdevicestate?view=graph-rest-beta) object.

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
PATCH /deviceManagement/hardwareConfigurations/{hardwareConfigurationId}/deviceRunStates/{hardwareConfigurationDeviceStateId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [hardwareConfigurationDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationdevicestate?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [hardwareConfigurationDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationdevicestate?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the hardware configuration script device state entity. This property is read-only. |
| deviceName | String | The name of the device |
| osVersion | String | Operating system version of the device \(E.g. 10.0.19042.1165, 10.0.19042.1288 etc.\) |
| upn | String | User Principal Name \(UPN\). |
| internalVersion | Int32 | The Policy internal version |
| lastStateUpdateDateTime | DateTimeOffset | The last timestamp of when the hardware configuration executed |
| configurationState | [runState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runstate?view=graph-rest-beta) | Configuration state from the lastest hardware configuration execution. Possible values are: `unknown`, `success`, `fail`, `scriptError`, `pending`, `notApplicable`. |
| configurationOutput | String | Output of the hardware configuration execution |
| configurationError | String | Error from the hardware configuration execution |
| assignmentFilterIds | String | A list of identifier strings of different assignment filters applied |
| userId | String | The unique identifier of the Entra user associated with the device for which policy is applied. Read-Only. |

## Response

If successful, this method returns a `200 OK` response code and an updated [hardwareConfigurationDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationdevicestate?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/hardwareConfigurations/{hardwareConfigurationId}/deviceRunStates/{hardwareConfigurationDeviceStateId}
Content-type: application/json
Content-length: 497

{
  "@odata.type": "#microsoft.graph.hardwareConfigurationDeviceState",
  "deviceName": "Device Name value",
  "osVersion": "Os Version value",
  "upn": "Upn value",
  "internalVersion": 15,
  "lastStateUpdateDateTime": "2017-01-01T00:02:58.4418045-08:00",
  "configurationState": "success",
  "configurationOutput": "Configuration Output value",
  "configurationError": "Configuration Error value",
  "assignmentFilterIds": "Assignment Filter Ids value",
  "userId": "User Id value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 546

{
  "@odata.type": "#microsoft.graph.hardwareConfigurationDeviceState",
  "id": "74b9fcd8-fcd8-74b9-d8fc-b974d8fcb974",
  "deviceName": "Device Name value",
  "osVersion": "Os Version value",
  "upn": "Upn value",
  "internalVersion": 15,
  "lastStateUpdateDateTime": "2017-01-01T00:02:58.4418045-08:00",
  "configurationState": "success",
  "configurationOutput": "Configuration Output value",
  "configurationError": "Configuration Error value",
  "assignmentFilterIds": "Assignment Filter Ids value",
  "userId": "User Id value"
}
```
