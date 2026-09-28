<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectionwipeaction-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Create windowsInformationProtectionWipeAction

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
POST /deviceAppManagement/windowsInformationProtectionWipeActions
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the windowsInformationProtectionWipeAction object.

The following table shows the properties that are required when you create the windowsInformationProtectionWipeAction.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| status | [actionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-actionstate?view=graph-rest-beta) | Wipe action status. Possible values are: `none`, `pending`, `canceled`, `active`, `done`, `failed`, `notSupported`. |
| targetedUserId | String | The UserId being targeted by this wipe action. |
| targetedDeviceRegistrationId | String | The DeviceRegistrationId being targeted by this wipe action. |
| targetedDeviceName | String | Targeted device name. |
| targetedDeviceMacAddress | String | Targeted device Mac address. |
| lastCheckInDateTime | DateTimeOffset | Last checkin time of the device that was targeted by this wipe action. |

## Response

If successful, this method returns a `201 Created` response code and a [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceAppManagement/windowsInformationProtectionWipeActions
Content-type: application/json
Content-length: 412

{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionWipeAction",
  "status": "pending",
  "targetedUserId": "Targeted User Id value",
  "targetedDeviceRegistrationId": "Targeted Device Registration Id value",
  "targetedDeviceName": "Targeted Device Name value",
  "targetedDeviceMacAddress": "Targeted Device Mac Address value",
  "lastCheckInDateTime": "2016-12-31T23:59:56.413532-08:00"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 461

{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionWipeAction",
  "id": "2620a996-a996-2620-96a9-202696a92026",
  "status": "pending",
  "targetedUserId": "Targeted User Id value",
  "targetedDeviceRegistrationId": "Targeted Device Registration Id value",
  "targetedDeviceName": "Targeted Device Name value",
  "targetedDeviceMacAddress": "Targeted Device Mac Address value",
  "lastCheckInDateTime": "2016-12-31T23:59:56.413532-08:00"
}
```
