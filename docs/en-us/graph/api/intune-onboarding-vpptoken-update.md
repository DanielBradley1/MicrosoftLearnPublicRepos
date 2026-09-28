<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-onboarding-vpptoken-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-10 -->

# Update vppToken

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementApps.ReadWrite.All, DeviceManagementServiceConfig.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementApps.ReadWrite.All, DeviceManagementServiceConfig.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceAppManagement/vppTokens/{vppTokenId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | This is automatically generated when the appleVolumePurchaseProgramToken is created. It is the Key of the entity. |
| organizationName | String | The organization associated with the Apple Volume Purchase Program Token |
| vppTokenAccountType | [vppTokenAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-vpptokenaccounttype?view=graph-rest-1.0) | The type of volume purchase program which the given Apple Volume Purchase Program Token is associated with. The possible values are: `business`, `education`. The possible values are: `business`, `education`. |
| appleId | String | The apple Id associated with the given Apple Volume Purchase Program Token. |
| expirationDateTime | DateTimeOffset | The expiration date time of the Apple Volume Purchase Program Token. |
| lastSyncDateTime | DateTimeOffset | The last time when an application sync was done with the Apple volume purchase program service using the the Apple Volume Purchase Program Token. |
| token | String | The Apple Volume Purchase Program Token string downloaded from the Apple Volume Purchase Program. |
| lastModifiedDateTime | DateTimeOffset | Last modification date time associated with the Apple Volume Purchase Program Token. |
| state | [vppTokenState](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokenstate?view=graph-rest-1.0) | Current state of the Apple Volume Purchase Program Token. The possible values are: `unknown`, `valid`, `expired`, `invalid`, `assignedToExternalMDM`. The possible values are: `unknown`, `valid`, `expired`, `invalid`, `assignedToExternalMDM`. |
| lastSyncStatus | [vppTokenSyncStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokensyncstatus?view=graph-rest-1.0) | Current sync status of the last application sync which was triggered using the Apple Volume Purchase Program Token. The possible values are: `none`, `inProgress`, `completed`, `failed`. The possible values are: `none`, `inProgress`, `completed`, `failed`. |
| automaticallyUpdateApps | Boolean | Whether or not apps for the VPP token will be automatically updated. |
| countryOrRegion | String | Whether or not apps for the VPP token will be automatically updated. |
| lastAppCount | Int32 | The number of apps under the Apple Volume Purchase Program Token since the last token sync. |

## Response

If successful, this method returns a `200 OK` response code and an updated [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceAppManagement/vppTokens/{vppTokenId}
Content-type: application/json
Content-length: 484

{
  "@odata.type": "#microsoft.graph.vppToken",
  "organizationName": "Organization Name value",
  "vppTokenAccountType": "education",
  "appleId": "Apple Id value",
  "expirationDateTime": "2016-12-31T23:57:57.2481234-08:00",
  "lastSyncDateTime": "2017-01-01T00:02:49.3205976-08:00",
  "token": "Token value",
  "state": "valid",
  "lastSyncStatus": "inProgress",
  "automaticallyUpdateApps": true,
  "countryOrRegion": "Country Or Region value",
  "lastAppCount": 12
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 597

{
  "@odata.type": "#microsoft.graph.vppToken",
  "id": "9ceb2f92-2f92-9ceb-922f-eb9c922feb9c",
  "organizationName": "Organization Name value",
  "vppTokenAccountType": "education",
  "appleId": "Apple Id value",
  "expirationDateTime": "2016-12-31T23:57:57.2481234-08:00",
  "lastSyncDateTime": "2017-01-01T00:02:49.3205976-08:00",
  "token": "Token value",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "state": "valid",
  "lastSyncStatus": "inProgress",
  "automaticallyUpdateApps": true,
  "countryOrRegion": "Country Or Region value",
  "lastAppCount": 12
}
```
