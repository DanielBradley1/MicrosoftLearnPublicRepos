<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountenterprisesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# androidManagedStoreAccountEnterpriseSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Enterprise settings for an Android managed store account.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get androidManagedStoreAccountEnterpriseSettings](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-get?view=graph-rest-beta) | [androidManagedStoreAccountEnterpriseSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountenterprisesettings?view=graph-rest-beta) | Read properties and relationships of the [androidManagedStoreAccountEnterpriseSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountenterprisesettings?view=graph-rest-beta) object. |
| [Update androidManagedStoreAccountEnterpriseSettings](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-update?view=graph-rest-beta) | [androidManagedStoreAccountEnterpriseSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountenterprisesettings?view=graph-rest-beta) | Update the properties of a [androidManagedStoreAccountEnterpriseSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountenterprisesettings?view=graph-rest-beta) object. |
| [approveApps action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-approveapps?view=graph-rest-beta) | None |  |
| [requestSignupUrl action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-requestsignupurl?view=graph-rest-beta) | String |  |
| [completeSignup action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-completesignup?view=graph-rest-beta) | None |  |
| [syncApps action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-syncapps?view=graph-rest-beta) | None |  |
| [unbind action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-unbind?view=graph-rest-beta) | None |  |
| [createGooglePlayWebToken action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-creategoogleplaywebtoken?view=graph-rest-beta) | String | Generates a web token that is used in an embeddable component. |
| [setAndroidDeviceOwnerFullyManagedEnrollmentState action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-setandroiddeviceownerfullymanagedenrollmentstate?view=graph-rest-beta) | None | Sets the AndroidManagedStoreAccountEnterpriseSettings AndroidDeviceOwnerFullyManagedEnrollmentEnabled to the given value. |
| [addApps action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-addapps?view=graph-rest-beta) | None |  |
| [retrieveStoreLayout function](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-retrievestorelayout?view=graph-rest-beta) | [androidManagedStoreLayoutType](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstorelayouttype?view=graph-rest-beta) | Gets the Managed Google Play store layout type from Google EMM API. |
| [setStoreLayout action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-setstorelayout?view=graph-rest-beta) | None | Sets the Managed Google Play store layout type via Google EMM API. |
| [requestEnterpriseUpgradeUrl action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreaccountenterprisesettings-requestenterpriseupgradeurl?view=graph-rest-beta) | String |  |

## Properties

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

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidManagedStoreAccountEnterpriseSettings",
  "id": "String (identifier)",
  "bindStatus": "String",
  "managedGooglePlayEnterpriseType": "String",
  "lastAppSyncDateTime": "String (timestamp)",
  "lastAppSyncStatus": "String",
  "ownerUserPrincipalName": "String",
  "ownerOrganizationName": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "enrollmentTarget": "String",
  "targetGroupIds": [
    "String"
  ],
  "deviceOwnerManagementEnabled": true,
  "companyCodes": [
    {
      "@odata.type": "microsoft.graph.androidEnrollmentCompanyCode",
      "enrollmentToken": "String",
      "qrCodeContent": "String",
      "qrCodeImage": {
        "@odata.type": "microsoft.graph.mimeContent",
        "type": "String",
        "value": "binary"
      }
    }
  ],
  "androidDeviceOwnerFullyManagedEnrollmentEnabled": true,
  "managedGooglePlayInitialScopeTagIds": [
    "String"
  ]
}
```
