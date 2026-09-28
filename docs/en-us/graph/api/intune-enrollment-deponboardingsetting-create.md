<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Create depOnboardingSetting

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementServiceConfig.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementServiceConfig.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/depOnboardingSettings
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the depOnboardingSetting object.

The following table shows the properties that are required when you create the depOnboardingSetting.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | UUID for the object |
| appleIdentifier | String | The Apple ID used to obtain the current token. |
| tokenExpirationDateTime | DateTimeOffset | When the token will expire. |
| lastModifiedDateTime | DateTimeOffset | When the service was onboarded. |
| lastSuccessfulSyncDateTime | DateTimeOffset | When the service last syned with Intune |
| lastSyncTriggeredDateTime | DateTimeOffset | When Intune last requested a sync. |
| shareTokenWithSchoolDataSyncService | Boolean | Whether or not the Dep token sharing is enabled with the School Data Sync service. |
| lastSyncErrorCode | Int32 | Error code reported by Apple during last dep sync. |
| tokenType | [depTokenType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptokentype?view=graph-rest-beta) | Gets or sets the Dep Token Type. Possible values are: `none`, `dep`, `appleSchoolManager`. |
| tokenName | String | Friendly Name for Dep Token |
| syncedDeviceCount | Int32 | Gets synced device count |
| dataSharingConsentGranted | Boolean | Consent granted for data sharing with Apple Dep Service |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. |

## Response

If successful, this method returns a `201 Created` response code and a [depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/depOnboardingSettings
Content-type: application/json
Content-length: 576

{
  "@odata.type": "#microsoft.graph.depOnboardingSetting",
  "appleIdentifier": "Apple Identifier value",
  "tokenExpirationDateTime": "2016-12-31T23:59:54.0590989-08:00",
  "lastSuccessfulSyncDateTime": "2017-01-01T00:03:28.120883-08:00",
  "lastSyncTriggeredDateTime": "2017-01-01T00:00:02.0916369-08:00",
  "shareTokenWithSchoolDataSyncService": true,
  "lastSyncErrorCode": 1,
  "tokenType": "dep",
  "tokenName": "Token Name value",
  "syncedDeviceCount": 1,
  "dataSharingConsentGranted": true,
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 689

{
  "@odata.type": "#microsoft.graph.depOnboardingSetting",
  "id": "40342229-2229-4034-2922-344029223440",
  "appleIdentifier": "Apple Identifier value",
  "tokenExpirationDateTime": "2016-12-31T23:59:54.0590989-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "lastSuccessfulSyncDateTime": "2017-01-01T00:03:28.120883-08:00",
  "lastSyncTriggeredDateTime": "2017-01-01T00:00:02.0916369-08:00",
  "shareTokenWithSchoolDataSyncService": true,
  "lastSyncErrorCode": 1,
  "tokenType": "dep",
  "tokenName": "Token Name value",
  "syncedDeviceCount": 1,
  "dataSharingConsentGranted": true,
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ]
}
```
