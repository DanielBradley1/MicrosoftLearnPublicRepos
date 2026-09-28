<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depiosenrollmentprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-13 -->

# depIOSEnrollmentProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The DepIOSEnrollmentProfile resource represents an Apple Device Enrollment Program \(DEP\) enrollment profile specific to iOS configuration. This type of profile must be assigned to Apple DEP serial numbers before the corresponding devices can enroll via DEP.

Inherits from [depEnrollmentBaseProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentbaseprofile?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List depIOSEnrollmentProfiles](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depiosenrollmentprofile-list?view=graph-rest-beta) | [depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depiosenrollmentprofile?view=graph-rest-beta) collection | List properties and relationships of the [depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depiosenrollmentprofile?view=graph-rest-beta) objects. |
| [Get depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depiosenrollmentprofile-get?view=graph-rest-beta) | [depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depiosenrollmentprofile?view=graph-rest-beta) | Read properties and relationships of the [depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depiosenrollmentprofile?view=graph-rest-beta) object. |
| [Create depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depiosenrollmentprofile-create?view=graph-rest-beta) | [depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depiosenrollmentprofile?view=graph-rest-beta) | Create a new [depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depiosenrollmentprofile?view=graph-rest-beta) object. |
| [Delete depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depiosenrollmentprofile-delete?view=graph-rest-beta) | None | Deletes a [depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depiosenrollmentprofile?view=graph-rest-beta). |
| [Update depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depiosenrollmentprofile-update?view=graph-rest-beta) | [depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depiosenrollmentprofile?view=graph-rest-beta) | Update the properties of a [depIOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depiosenrollmentprofile?view=graph-rest-beta) object. |

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
| iTunesPairingMode | [iTunesPairingMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-itunespairingmode?view=graph-rest-beta) | Indicates the iTunes pairing mode. Possible values are: `disallow`, `allow`, `requiresCertificate`. |
| managementCertificates | [managementCertificateWithThumbprint](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-managementcertificatewiththumbprint?view=graph-rest-beta) collection | Management certificates for Apple Configurator |
| restoreFromAndroidDisabled | Boolean | Indicates if Restore from Android is disabled |
| awaitDeviceConfiguredConfirmation | Boolean | Indicates if the device will need to wait for configured confirmation |
| sharedIPadMaximumUserCount | Int32 | This specifies the maximum number of users that can use a shared iPad. Only applicable in shared iPad mode. |
| enableSharedIPad | Boolean | This indicates whether the device is to be enrolled in a mode which enables multi user scenarios. Only applicable in shared iPads. |
| companyPortalVppTokenId | String | If set, indicates which Vpp token should be used to deploy the Company Portal w/ device licensing. 'enableAuthenticationViaCompanyPortal' must be set in order for this property to be set. |
| enableSingleAppEnrollmentMode | Boolean | Tells the device to enable single app mode and apply app-lock during enrollment. Default is false. 'enableAuthenticationViaCompanyPortal' and 'companyPortalVppTokenId' must be set for this property to be set. |
| homeButtonScreenDisabled | Boolean | Indicates if home button sensitivity screen is disabled |
| iMessageAndFaceTimeScreenDisabled | Boolean | Indicates if iMessage and FaceTime screen is disabled |
| onBoardingScreenDisabled | Boolean | Indicates if onboarding setup screen is disabled |
| simSetupScreenDisabled | Boolean | Indicates if the SIMSetup screen is disabled |
| softwareUpdateScreenDisabled | Boolean | Indicates if the mandatory sofware update screen is disabled |
| watchMigrationScreenDisabled | Boolean | Indicates if the watch migration screen is disabled |
| appearanceScreenDisabled | Boolean | Indicates if Apperance screen is disabled |
| expressLanguageScreenDisabled | Boolean | Indicates if Express Language screen is disabled |
| preferredLanguageScreenDisabled | Boolean | Indicates if Preferred language screen is disabled |
| deviceToDeviceMigrationDisabled | Boolean | Indicates if Device To Device Migration is disabled |
| welcomeScreenDisabled | Boolean | Indicates if Weclome screen is disabled |
| passCodeDisabled | Boolean | Indicates if Passcode setup pane is disabled |
| zoomDisabled | Boolean | Indicates if zoom setup pane is disabled |
| restoreCompletedScreenDisabled | Boolean | Indicates if Weclome screen is disabled |
| updateCompleteScreenDisabled | Boolean | Indicates if Weclome screen is disabled |
| forceTemporarySession | Boolean | Indicates if temporary sessions is enabled |
| temporarySessionTimeoutInSeconds | Int32 | Indicates timeout of temporary session |
| userSessionTimeoutInSeconds | Int32 | Indicates timeout of temporary session |
| passcodeLockGracePeriodInSeconds | Int32 | Indicates timeout before locked screen requires the user to enter the device passocde to unlock it |
| carrierActivationUrl | String | Carrier URL for activating device eSIM. |
| userlessSharedAadModeEnabled | Boolean | Indicates that this apple device is designated to support 'shared device mode' scenarios. This is distinct from the 'shared iPad' scenario. See [https://learn.microsoft.com/mem/intune/enrollment/device-enrollment-shared-ios\|](https://learn.microsoft.com/en-us/mem/intune/enrollment/device-enrollment-shared-ios%7C) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.depIOSEnrollmentProfile",
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
  "iTunesPairingMode": "String",
  "managementCertificates": [
    {
      "@odata.type": "microsoft.graph.managementCertificateWithThumbprint",
      "thumbprint": "String",
      "certificate": "String"
    }
  ],
  "restoreFromAndroidDisabled": true,
  "awaitDeviceConfiguredConfirmation": true,
  "sharedIPadMaximumUserCount": 1024,
  "enableSharedIPad": true,
  "companyPortalVppTokenId": "String",
  "enableSingleAppEnrollmentMode": true,
  "homeButtonScreenDisabled": true,
  "iMessageAndFaceTimeScreenDisabled": true,
  "onBoardingScreenDisabled": true,
  "simSetupScreenDisabled": true,
  "softwareUpdateScreenDisabled": true,
  "watchMigrationScreenDisabled": true,
  "appearanceScreenDisabled": true,
  "expressLanguageScreenDisabled": true,
  "preferredLanguageScreenDisabled": true,
  "deviceToDeviceMigrationDisabled": true,
  "welcomeScreenDisabled": true,
  "passCodeDisabled": true,
  "zoomDisabled": true,
  "restoreCompletedScreenDisabled": true,
  "updateCompleteScreenDisabled": true,
  "forceTemporarySession": true,
  "temporarySessionTimeoutInSeconds": 1024,
  "userSessionTimeoutInSeconds": 1024,
  "passcodeLockGracePeriodInSeconds": 1024,
  "carrierActivationUrl": "String",
  "userlessSharedAadModeEnabled": true
}
```
