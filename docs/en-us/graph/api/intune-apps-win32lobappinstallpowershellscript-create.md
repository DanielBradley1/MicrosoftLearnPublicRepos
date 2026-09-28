<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-apps-win32lobappinstallpowershellscript-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-12 -->

# Create win32LobAppInstallPowerShellScript

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [win32LobAppInstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappinstallpowershellscript?view=graph-rest-beta) object.

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
POST /deviceAppManagement/mobileApps/{mobileAppId}/contentVersions/{mobileAppContentId}/scripts
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the win32LobAppInstallPowerShellScript object.

The following table shows the properties that are required when you create the win32LobAppInstallPowerShellScript.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the script associated with a mobileLobApp entity. This property is read-only. Inherited from [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta) |
| displayName | String | The display name for the script. Inherited from [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta) |
| content | String | The content of the script. This is a Base64-encoded representation of the script's original content. The content has a maximum size limit of 100KB. Inherited from [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta) |
| state | [mobileAppContentScriptState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscriptstate?view=graph-rest-beta) | Indicates the state of the script upload. Possible values are commitPending, commitSuccess, and commitFailed. This property is read-only. Inherited from [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta). Possible values are: `commitPending`, `commitSuccess`, `commitFailed`, `unknownFutureValue`. |
| enforceSignatureCheck | Boolean | Indicates whether or not to enforce a signature check when running the script. When TRUE, the script cannot be run without enforcing a signature check. When FALSE, no signature check will be enforced when running the script. Default value is FALSE. Inherited from [win32LobAppScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappscript?view=graph-rest-beta) |
| runAs32Bit | Boolean | Indicates whether the script will run as 32-bit or 64-bit. When TRUE, the script will run as 32-bit. When FALSE, the script will run as 64-bit. Default value is FALSE. Inherited from [win32LobAppScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappscript?view=graph-rest-beta) |

## Response

If successful, this method returns a `201 Created` response code and a [win32LobAppInstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappinstallpowershellscript?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceAppManagement/mobileApps/{mobileAppId}/contentVersions/{mobileAppContentId}/scripts
Content-type: application/json
Content-length: 233

{
  "@odata.type": "#microsoft.graph.win32LobAppInstallPowerShellScript",
  "displayName": "Display Name value",
  "content": "Content value",
  "state": "commitSuccess",
  "enforceSignatureCheck": true,
  "runAs32Bit": true
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 282

{
  "@odata.type": "#microsoft.graph.win32LobAppInstallPowerShellScript",
  "id": "a125f813-f813-a125-13f8-25a113f825a1",
  "displayName": "Display Name value",
  "content": "Content value",
  "state": "commitSuccess",
  "enforceSignatureCheck": true,
  "runAs32Bit": true
}
```
