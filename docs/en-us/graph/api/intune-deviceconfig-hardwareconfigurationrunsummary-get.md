<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationrunsummary-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Get hardwareConfigurationRunSummary

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Read properties and relationships of the [hardwareConfigurationRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationrunsummary?view=graph-rest-beta) object.

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
GET /deviceManagement/hardwareConfigurations/{hardwareConfigurationId}/runSummary
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

If successful, this method returns a `200 OK` response code and [hardwareConfigurationRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationrunsummary?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/deviceManagement/hardwareConfigurations/{hardwareConfigurationId}/runSummary
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 567

{
  "value": {
    "@odata.type": "#microsoft.graph.hardwareConfigurationRunSummary",
    "id": "76b964f2-64f2-76b9-f264-b976f264b976",
    "successfulDeviceCount": 5,
    "failedDeviceCount": 1,
    "pendingDeviceCount": 2,
    "errorDeviceCount": 0,
    "notApplicableDeviceCount": 8,
    "unknownDeviceCount": 2,
    "successfulUserCount": 3,
    "failedUserCount": 15,
    "pendingUserCount": 0,
    "errorUserCount": 14,
    "notApplicableUserCount": 6,
    "unknownUserCount": 0,
    "lastRunDateTime": "2016-12-31T23:57:28.499537-08:00"
  }
}
```
