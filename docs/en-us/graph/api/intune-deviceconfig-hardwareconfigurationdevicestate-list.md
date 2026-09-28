<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationdevicestate-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# List hardwareConfigurationDeviceStates

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

List properties and relationships of the [hardwareConfigurationDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationdevicestate?view=graph-rest-beta) objects.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.Read.All, DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
GET /deviceManagement/hardwareConfigurations/{hardwareConfigurationId}/deviceRunStates
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [hardwareConfigurationDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationdevicestate?view=graph-rest-beta) objects in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/deviceManagement/hardwareConfigurations/{hardwareConfigurationId}/deviceRunStates
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 627

{
  "value": [
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
  ]
}
```
