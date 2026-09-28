<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# depOnboardingSetting resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The depOnboardingSetting represents an instance of the Apple DEP service being onboarded to Intune. The onboarded service instance manages an Apple Token used to synchronize data between Apple and Intune.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List depOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-list?view=graph-rest-beta) | [depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta) collection | List properties and relationships of the [depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta) objects. |
| [Get depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-get?view=graph-rest-beta) | [depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta) | Read properties and relationships of the [depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta) object. |
| [Create depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-create?view=graph-rest-beta) | [depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta) | Create a new [depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta) object. |
| [Delete depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-delete?view=graph-rest-beta) | None | Deletes a [depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta). |
| [Update depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-update?view=graph-rest-beta) | [depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta) | Update the properties of a [depOnboardingSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deponboardingsetting?view=graph-rest-beta) object. |
| [getEncryptionPublicKey function](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-getencryptionpublickey?view=graph-rest-beta) | String | Get a public key to use to encrypt the Apple device enrollment program token |
| [generateEncryptionPublicKey action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-generateencryptionpublickey?view=graph-rest-beta) | String | Generate a public key to use to encrypt the Apple device enrollment program token |
| [uploadDepToken action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-uploaddeptoken?view=graph-rest-beta) | None | Uploads a new Device Enrollment Program token |
| [syncWithAppleDeviceEnrollmentProgram action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-syncwithappledeviceenrollmentprogram?view=graph-rest-beta) | None | Synchronizes between Apple Device Enrollment Program and Intune |
| [shareForSchoolDataSyncService action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-shareforschooldatasyncservice?view=graph-rest-beta) | None |  |
| [unshareForSchoolDataSyncService action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-unshareforschooldatasyncservice?view=graph-rest-beta) | None |  |
| [getExpiringVppTokenCount function](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-getexpiringvpptokencount?view=graph-rest-beta) | Int32 |  |
| [releaseAppleDevices action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deponboardingsetting-releaseappledevices?view=graph-rest-beta) | None |  |

## Properties

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

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| defaultIosEnrollmentProfile | [depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depiosenrollmentprofile?view=graph-rest-beta) | Default iOS Enrollment Profile |
| defaultMacOsEnrollmentProfile | [depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depmacosenrollmentprofile?view=graph-rest-beta) | Default MacOs Enrollment Profile |
| defaultVisionOSEnrollmentProfile | [depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depvisionosenrollmentprofile?view=graph-rest-beta) | Default VisionOS Enrollment Profile |
| defaultTvOSEnrollmentProfile | [depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptvosenrollmentprofile?view=graph-rest-beta) | Default TvOS Enrollment Profile |
| enrollmentProfiles | [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) collection | The enrollment profiles. |
| importedAppleDeviceIdentities | [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) collection | The imported Apple device identities. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.depOnboardingSetting",
  "id": "String (identifier)",
  "appleIdentifier": "String",
  "tokenExpirationDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "lastSuccessfulSyncDateTime": "String (timestamp)",
  "lastSyncTriggeredDateTime": "String (timestamp)",
  "shareTokenWithSchoolDataSyncService": true,
  "lastSyncErrorCode": 1024,
  "tokenType": "String",
  "tokenName": "String",
  "syncedDeviceCount": 1024,
  "dataSharingConsentGranted": true,
  "roleScopeTagIds": [
    "String"
  ]
}
```
