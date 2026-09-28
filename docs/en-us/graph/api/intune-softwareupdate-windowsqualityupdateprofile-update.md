<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdateprofile-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update windowsQualityUpdateProfile

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta) object.

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
PATCH /deviceManagement/windowsQualityUpdateProfiles/{windowsQualityUpdateProfileId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The Intune policy id. |
| displayName | String | The display name for the profile. |
| description | String | The description of the profile which is specified by the user. |
| expeditedUpdateSettings | [expeditedWindowsQualityUpdateSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-expeditedwindowsqualityupdatesettings?view=graph-rest-beta) | Expedited update settings. |
| createdDateTime | DateTimeOffset | The date time that the profile was created. |
| lastModifiedDateTime | DateTimeOffset | The date time that the profile was last modified. |
| roleScopeTagIds | String collection | List of Scope Tags for this Quality Update entity. |
| releaseDateDisplayName | String | Friendly release date to display for a Quality Update release |
| deployableContentDisplayName | String | Friendly display name of the quality update profile deployable content |

## Response

If successful, this method returns a `200 OK` response code and an updated [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/windowsQualityUpdateProfiles/{windowsQualityUpdateProfileId}
Content-type: application/json
Content-length: 558

{
  "@odata.type": "#microsoft.graph.windowsQualityUpdateProfile",
  "displayName": "Display Name value",
  "description": "Description value",
  "expeditedUpdateSettings": {
    "@odata.type": "microsoft.graph.expeditedWindowsQualityUpdateSettings",
    "qualityUpdateRelease": "Quality Update Release value",
    "daysUntilForcedReboot": 5
  },
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "releaseDateDisplayName": "Release Date Display Name value",
  "deployableContentDisplayName": "Deployable Content Display Name value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 730

{
  "@odata.type": "#microsoft.graph.windowsQualityUpdateProfile",
  "id": "76fc7b65-7b65-76fc-657b-fc76657bfc76",
  "displayName": "Display Name value",
  "description": "Description value",
  "expeditedUpdateSettings": {
    "@odata.type": "microsoft.graph.expeditedWindowsQualityUpdateSettings",
    "qualityUpdateRelease": "Quality Update Release value",
    "daysUntilForcedReboot": 5
  },
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "releaseDateDisplayName": "Release Date Display Name value",
  "deployableContentDisplayName": "Deployable Content Display Name value"
}
```
