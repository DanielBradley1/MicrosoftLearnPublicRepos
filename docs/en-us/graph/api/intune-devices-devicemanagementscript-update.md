<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscript-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Update deviceManagementScript

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [deviceManagementScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementscript?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementScripts.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementScripts.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/deviceManagementScripts/{deviceManagementScriptId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [deviceManagementScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementscript?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [deviceManagementScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementscript?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| enforceSignatureCheck | Boolean | Indicate whether the script signature needs be checked. |
| runAs32Bit | Boolean | A value indicating whether the PowerShell script should run as 32-bit |
| id | String | Unique Identifier for the device management script. |
| displayName | String | Name of the device management script. |
| description | String | Optional description for the device management script. |
| scriptContent | Binary | The script content. |
| createdDateTime | DateTimeOffset | The date and time the device management script was created. This property is read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time the device management script was last modified. This property is read-only. |
| runAsAccount | [runAsAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runasaccounttype?view=graph-rest-beta) | Indicates the type of execution context. Possible values are: `system`, `user`. |
| fileName | String | Script file name. |
| roleScopeTagIds | String collection | List of Scope Tag IDs for this PowerShellScript instance. |

## Response

If successful, this method returns a `200 OK` response code and an updated [deviceManagementScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementscript?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/deviceManagementScripts/{deviceManagementScriptId}
Content-type: application/json
Content-length: 367

{
  "@odata.type": "#microsoft.graph.deviceManagementScript",
  "enforceSignatureCheck": true,
  "runAs32Bit": true,
  "displayName": "Display Name value",
  "description": "Description value",
  "scriptContent": "c2NyaXB0Q29udGVudA==",
  "runAsAccount": "user",
  "fileName": "File Name value",
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 539

{
  "@odata.type": "#microsoft.graph.deviceManagementScript",
  "enforceSignatureCheck": true,
  "runAs32Bit": true,
  "id": "59ea4525-4525-59ea-2545-ea592545ea59",
  "displayName": "Display Name value",
  "description": "Description value",
  "scriptContent": "c2NyaXB0Q29udGVudA==",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "runAsAccount": "user",
  "fileName": "File Name value",
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ]
}
```
