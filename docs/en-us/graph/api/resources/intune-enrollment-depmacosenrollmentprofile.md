<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depmacosenrollmentprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-09 -->

# depMacOSEnrollmentProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The DepMacOSEnrollmentProfile resource represents an Apple Device Enrollment Program \(DEP\) enrollment profile specific to macOS configuration. This type of profile must be assigned to Apple DEP serial numbers before the corresponding devices can enroll via DEP.

Inherits from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List depMacOSEnrollmentProfiles](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depmacosenrollmentprofile-list?view=graph-rest-beta) | [depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depmacosenrollmentprofile?view=graph-rest-beta) collection | List properties and relationships of the [depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depmacosenrollmentprofile?view=graph-rest-beta) objects. |
| [Get depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depmacosenrollmentprofile-get?view=graph-rest-beta) | [depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depmacosenrollmentprofile?view=graph-rest-beta) | Read properties and relationships of the [depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depmacosenrollmentprofile?view=graph-rest-beta) object. |
| [Create depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depmacosenrollmentprofile-create?view=graph-rest-beta) | [depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depmacosenrollmentprofile?view=graph-rest-beta) | Create a new [depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depmacosenrollmentprofile?view=graph-rest-beta) object. |
| [Delete depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depmacosenrollmentprofile-delete?view=graph-rest-beta) | None | Deletes a [depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depmacosenrollmentprofile?view=graph-rest-beta). |
| [Update depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depmacosenrollmentprofile-update?view=graph-rest-beta) | [depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depmacosenrollmentprofile?view=graph-rest-beta) | Update the properties of a [depMacOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depmacosenrollmentprofile?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| displayName | String | Name of the profile Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| description | String | Description of the profile Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| requiresUserAuthentication | Boolean | Indicates if the profile requires user authentication Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| configurationEndpointUrl | String | Configuration endpoint url to use for Enrollment Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| enableAuthenticationViaCompanyPortal | Boolean | Indicates to authenticate with Apple Setup Assistant instead of Company Portal. Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| requireCompanyPortalOnSetupAssistantEnrolledDevices | Boolean | Indicates that Company Portal is required on setup assistant enrolled devices Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| isDefault | Boolean | Indicates if this is the default profile Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| supervisedModeEnabled | Boolean | Supervised mode, True to enable, false otherwise. See [https://learn.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune](https://learn.microsoft.com/en-us/intune/deploy-use/enroll-devices-in-microsoft-intune) for additional information. Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| supportDepartment | String | Support department information Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| isMandatory | Boolean | Indicates if the profile is mandatory Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| locationDisabled | Boolean | Indicates if Location service setup pane is disabled Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| supportPhoneNumber | String | Support phone number Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| profileRemovalDisabled | Boolean | Indicates if the profile removal option is disabled Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| restoreBlocked | Boolean | Indicates if Restore setup pane is blocked Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| appleIdDisabled | Boolean | Indicates if Apple id setup pane is disabled Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| termsAndConditionsDisabled | Boolean | Indicates if 'Terms and Conditions' setup pane is disabled Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| touchIdDisabled | Boolean | Indicates if touch id setup pane is disabled Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| applePayDisabled | Boolean | Indicates if Apple pay setup pane is disabled Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| siriDisabled | Boolean | Indicates if siri setup pane is disabled Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| diagnosticsDisabled | Boolean | Indicates if diagnostics setup pane is disabled Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| displayToneSetupDisabled | Boolean | Indicates if displaytone setup screen is disabled Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| privacyPaneDisabled | Boolean | Indicates if privacy screen is disabled Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| screenTimeScreenDisabled | Boolean | Indicates if screen timeout setup is disabled Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| deviceNameTemplate | String | Sets a literal or name pattern. Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| configurationWebUrl | Boolean | URL for setup assistant login Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| enabledSkipKeys | String collection | enabledSkipKeys contains all the enabled skip keys as strings Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| enrollmentTimeAzureAdGroupIds | Guid collection | EnrollmentTimeAzureAdGroupIds contains list of enrollment time Azure Group Ids to be associated with profile Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| waitForDeviceConfiguredConfirmation | Boolean | Indicates if the device will need to wait for configured confirmation Inherited from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta) |
| registrationDisabled | Boolean | Indicates if registration is disabled |
| fileVaultDisabled | Boolean | Indicates if file vault is disabled |
| iCloudDiagnosticsDisabled | Boolean | Indicates if iCloud Analytics screen is disabled |
| passCodeDisabled | Boolean | Indicates if Passcode setup pane is disabled |
| zoomDisabled | Boolean | Indicates if zoom setup pane is disabled |
| iCloudStorageDisabled | Boolean | Indicates if iCloud Documents and Desktop screen is disabled |
| chooseYourLockScreenDisabled | Boolean | Indicates if iCloud Documents and Desktop screen is disabled |
| accessibilityScreenDisabled | Boolean | Indicates if Accessibility screen is disabled |
| autoUnlockWithWatchDisabled | Boolean | Indicates if UnlockWithWatch screen is disabled |
| skipPrimarySetupAccountCreation | Boolean | Indicates whether Setup Assistant will skip the user interface for primary account setup |
| setPrimarySetupAccountAsRegularUser | Boolean | Indicates whether Setup Assistant will set the account as a regular user |
| dontAutoPopulatePrimaryAccountInfo | Boolean | Indicates whether Setup Assistant will auto populate the primary account information |
| primaryAccountFullName | String | Indicates what the full name for the primary account is |
| primaryAccountUserName | String | Indicates what the account name for the primary account is |
| enableRestrictEditing | Boolean | Indicates whether the user will enable blockediting |
| adminAccountUserName | String | Indicates what the user name for the admin account is |
| adminAccountFullName | String | Indicates what the full name for the admin account is |
| adminAccountPassword | String | Indicates what the password for the admin account is |
| hideAdminAccount | Boolean | Indicates whether the admin account should be hidded or not |
| requestRequiresNetworkTether | Boolean | Indicates if the device is network-tethered to run the command |
| autoAdvanceSetupEnabled | Boolean | Indicates if Setup Assistant will automatically advance through its screen |
| depProfileAdminAccountPasswordRotationSetting | [depProfileAdminAccountPasswordRotationSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depprofileadminaccountpasswordrotationsetting?view=graph-rest-beta) | Settings for local admin account password automatic rotation. |
| usePlatformSSODuringSetupAssistant | Boolean | Indicates whether Platform SSO is used as part of device enrollment during Setup Assistant. When TRUE, Platform SSO is used in device enrollment during Setup Assistant. When FALSE Platform SSO is not used in enrollment during Setup Assistant. Note: This value cannot be TRUE when configurationWebUrl is TRUE. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.depMacOSEnrollmentProfile",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "requiresUserAuthentication": true,
  "configurationEndpointUrl": "String",
  "enableAuthenticationViaCompanyPortal": true,
  "requireCompanyPortalOnSetupAssistantEnrolledDevices": true,
  "isDefault": true,
  "supervisedModeEnabled": true,
  "supportDepartment": "String",
  "isMandatory": true,
  "locationDisabled": true,
  "supportPhoneNumber": "String",
  "profileRemovalDisabled": true,
  "restoreBlocked": true,
  "appleIdDisabled": true,
  "termsAndConditionsDisabled": true,
  "touchIdDisabled": true,
  "applePayDisabled": true,
  "siriDisabled": true,
  "diagnosticsDisabled": true,
  "displayToneSetupDisabled": true,
  "privacyPaneDisabled": true,
  "screenTimeScreenDisabled": true,
  "deviceNameTemplate": "String",
  "configurationWebUrl": true,
  "enabledSkipKeys": [
    "String"
  ],
  "enrollmentTimeAzureAdGroupIds": [
    "Guid"
  ],
  "waitForDeviceConfiguredConfirmation": true,
  "registrationDisabled": true,
  "fileVaultDisabled": true,
  "iCloudDiagnosticsDisabled": true,
  "passCodeDisabled": true,
  "zoomDisabled": true,
  "iCloudStorageDisabled": true,
  "chooseYourLockScreenDisabled": true,
  "accessibilityScreenDisabled": true,
  "autoUnlockWithWatchDisabled": true,
  "skipPrimarySetupAccountCreation": true,
  "setPrimarySetupAccountAsRegularUser": true,
  "dontAutoPopulatePrimaryAccountInfo": true,
  "primaryAccountFullName": "String",
  "primaryAccountUserName": "String",
  "enableRestrictEditing": true,
  "adminAccountUserName": "String",
  "adminAccountFullName": "String",
  "adminAccountPassword": "String",
  "hideAdminAccount": true,
  "requestRequiresNetworkTether": true,
  "autoAdvanceSetupEnabled": true,
  "depProfileAdminAccountPasswordRotationSetting": {
    "@odata.type": "microsoft.graph.depProfileAdminAccountPasswordRotationSetting",
    "autoRotationPeriodInDays": 1024,
    "depProfileDelayAutoRotationSetting": {
      "@odata.type": "microsoft.graph.depProfileDelayAutoRotationSetting",
      "onRetrievalAutoRotatePasswordEnabled": true,
      "onRetrievalDelayAutoRotatePasswordInHours": 1024
    }
  },
  "usePlatformSSODuringSetupAssistant": true
}
```
