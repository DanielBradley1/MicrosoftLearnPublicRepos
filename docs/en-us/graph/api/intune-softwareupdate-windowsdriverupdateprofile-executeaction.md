<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofile-executeaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# executeAction action

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

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
POST /deviceManagement/windowsDriverUpdateProfiles/{windowsDriverUpdateProfileId}/executeAction
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Property | Type | Description |
| :--- | :--- | :--- |
| actionName | [driverApprovalAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-driverapprovalaction?view=graph-rest-beta) |  |
| driverIds | String collection |  |
| deploymentDate | DateTimeOffset |  |

## Response

If successful, this action returns a `200 OK` response code and a [bulkDriverActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-bulkdriveractionresult?view=graph-rest-beta) in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/windowsDriverUpdateProfiles/{windowsDriverUpdateProfileId}/executeAction

Content-type: application/json
Content-length: 137

{
  "actionName": "decline",
  "driverIds": [
    "Driver Ids value"
  ],
  "deploymentDate": "2016-12-31T23:58:18.3419405-08:00"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 298

{
  "value": {
    "@odata.type": "microsoft.graph.bulkDriverActionResult",
    "successfulDriverIds": [
      "Successful Driver Ids value"
    ],
    "failedDriverIds": [
      "Failed Driver Ids value"
    ],
    "notFoundDriverIds": [
      "Not Found Driver Ids value"
    ]
  }
}
```
