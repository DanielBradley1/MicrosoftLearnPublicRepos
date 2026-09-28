<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-chromebooksync-chromeosonboardingsettings-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update chromeOSOnboardingSettings

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta) object.

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
PATCH /deviceManagement/chromeOSOnboardingSettings/{chromeOSOnboardingSettingsId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ChromebookTenant's Id |
| ownerUserPrincipalName | String | The ChromebookTenant's OwnerUserPrincipalName |
| onboardingStatus | [onboardingStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-onboardingstatus?view=graph-rest-beta) | The ChromebookTenant's OnboardingStatus. Possible values are: `unknown`, `inprogress`, `onboarded`, `failed`, `offboarding`, `unknownFutureValue`. |
| lastModifiedDateTime | DateTimeOffset | The ChromebookTenant's LastModifiedDateTime |
| lastDirectorySyncDateTime | DateTimeOffset | The ChromebookTenant's LastDirectorySyncDateTime |

## Response

If successful, this method returns a `200 OK` response code and an updated [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/chromeOSOnboardingSettings/{chromeOSOnboardingSettingsId}
Content-type: application/json
Content-length: 238

{
  "@odata.type": "#microsoft.graph.chromeOSOnboardingSettings",
  "ownerUserPrincipalName": "Owner User Principal Name value",
  "onboardingStatus": "inprogress",
  "lastDirectorySyncDateTime": "2016-12-31T23:57:56.1183185-08:00"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 351

{
  "@odata.type": "#microsoft.graph.chromeOSOnboardingSettings",
  "id": "0344255d-255d-0344-5d25-44035d254403",
  "ownerUserPrincipalName": "Owner User Principal Name value",
  "onboardingStatus": "inprogress",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "lastDirectorySyncDateTime": "2016-12-31T23:57:56.1183185-08:00"
}
```
