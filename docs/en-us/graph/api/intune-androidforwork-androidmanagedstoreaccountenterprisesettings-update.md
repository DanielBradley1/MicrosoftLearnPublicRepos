<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Update androidManagedStoreAccountEnterpriseSettings

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [androidManagedStoreAccountEnterpriseSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountenterprisesettings?view=graph-rest-beta) object.

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
PATCH /deviceManagement/androidManagedStoreAccountEnterpriseSettings
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [androidManagedStoreAccountEnterpriseSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountenterprisesettings?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [androidManagedStoreAccountEnterpriseSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountenterprisesettings?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The Android store account enterprise settings identifier |
| bindStatus | [androidManagedStoreAccountBindStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountbindstatus?view=graph-rest-beta) | Bind status of the tenant with the Google EMM API. Possible values are: `notBound`, `bound`, `boundAndValidated`, `unbinding`. |
| managedGooglePlayEnterpriseType | [managedGooglePlayEnterpriseType](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-managedgoogleplayenterprisetype?view=graph-rest-beta) | The managed Google Play enterprise type associated with a tenant. Possible values are: unspecified, managedGoogleDomain, managedGooglePlayAccountsEnterprise. Default is: unspecified. Read-Only. Possible values are: `enterpriseTypeUnspecified`, `managedGoogleDomain`, `managedGooglePlayAccountsEnterprise`, `unknownFutureValue`. |
| lastAppSyncDateTime | DateTimeOffset | Last completion time for app sync |
| lastAppSyncStatus | [androidManagedStoreAccountAppSyncStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountappsyncstatus?view=graph-rest-beta) | Last application sync result. Possible values are: `success`, `credentialsNotValid`, `androidForWorkApiError`, `managementServiceError`, `unknownError`, `none`. |
| ownerUserPrincipalName | String | Owner UPN that created the enterprise |
| ownerOrganizationName | String | Organization name used when onboarding Android Enterprise |
| lastModifiedDateTime | DateTimeOffset | Last modification time for Android enterprise settings |
| enrollmentTarget | [androidManagedStoreAccountEnrollmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountenrollmenttarget?view=graph-rest-beta) | Indicates which users can enroll devices in Android Enterprise device management. Possible values are: `none`, `all`, `targeted`, `targetedAsEnrollmentRestrictions`. |
| targetGroupIds | String collection | Specifies which AAD groups can enroll devices in Android for Work device management if enrollmentTarget is set to 'Targeted' |
| deviceOwnerManagementEnabled | Boolean | Indicates if this account is flighting for Android Device Owner Management with CloudDPC. |
| companyCodes | [androidEnrollmentCompanyCode](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidenrollmentcompanycode?view=graph-rest-beta) collection | Company codes for AndroidManagedStoreAccountEnterpriseSettings |
| androidDeviceOwnerFullyManagedEnrollmentEnabled | Boolean | Company codes for AndroidManagedStoreAccountEnterpriseSettings |
| managedGooglePlayInitialScopeTagIds | String collection | Initial scope tags for MGP apps |

## Response

If successful, this method returns a `200 OK` response code and an updated [androidManagedStoreAccountEnterpriseSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountenterprisesettings?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/androidManagedStoreAccountEnterpriseSettings
Content-type: application/json
Content-length: 1063

{
  "@odata.type": "#microsoft.graph.androidManagedStoreAccountEnterpriseSettings",
  "bindStatus": "bound",
  "managedGooglePlayEnterpriseType": "managedGoogleDomain",
  "lastAppSyncDateTime": "2016-12-31T23:57:22.8606813-08:00",
  "lastAppSyncStatus": "credentialsNotValid",
  "ownerUserPrincipalName": "Owner User Principal Name value",
  "ownerOrganizationName": "Owner Organization Name value",
  "enrollmentTarget": "all",
  "targetGroupIds": [
    "Target Group Ids value"
  ],
  "deviceOwnerManagementEnabled": true,
  "companyCodes": [
    {
      "@odata.type": "microsoft.graph.androidEnrollmentCompanyCode",
      "enrollmentToken": "Enrollment Token value",
      "qrCodeContent": "Qr Code Content value",
      "qrCodeImage": {
        "@odata.type": "microsoft.graph.mimeContent",
        "type": "Type value",
        "value": "dmFsdWU="
      }
    }
  ],
  "androidDeviceOwnerFullyManagedEnrollmentEnabled": true,
  "managedGooglePlayInitialScopeTagIds": [
    "Managed Google Play Initial Scope Tag Ids value"
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1176

{
  "@odata.type": "#microsoft.graph.androidManagedStoreAccountEnterpriseSettings",
  "id": "b71357c9-57c9-b713-c957-13b7c95713b7",
  "bindStatus": "bound",
  "managedGooglePlayEnterpriseType": "managedGoogleDomain",
  "lastAppSyncDateTime": "2016-12-31T23:57:22.8606813-08:00",
  "lastAppSyncStatus": "credentialsNotValid",
  "ownerUserPrincipalName": "Owner User Principal Name value",
  "ownerOrganizationName": "Owner Organization Name value",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "enrollmentTarget": "all",
  "targetGroupIds": [
    "Target Group Ids value"
  ],
  "deviceOwnerManagementEnabled": true,
  "companyCodes": [
    {
      "@odata.type": "microsoft.graph.androidEnrollmentCompanyCode",
      "enrollmentToken": "Enrollment Token value",
      "qrCodeContent": "Qr Code Content value",
      "qrCodeImage": {
        "@odata.type": "microsoft.graph.mimeContent",
        "type": "Type value",
        "value": "dmFsdWU="
      }
    }
  ],
  "androidDeviceOwnerFullyManagedEnrollmentEnabled": true,
  "managedGooglePlayInitialScopeTagIds": [
    "Managed Google Play Initial Scope Tag Ids value"
  ]
}
```
