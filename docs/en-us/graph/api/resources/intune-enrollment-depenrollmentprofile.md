<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# depEnrollmentProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The depEnrollmentProfile resource represents an Apple Device Enrollment Program \(DEP\) enrollment profile. This type of profile must be assigned to Apple DEP serial numbers before the corresponding devices can enroll via DEP.

Inherits from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List depEnrollmentProfiles](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depenrollmentprofile-list?view=graph-rest-beta) | [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta) collection | List properties and relationships of the [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta) objects. |
| [Get depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depenrollmentprofile-get?view=graph-rest-beta) | [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta) | Read properties and relationships of the [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta) object. |
| [Create depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depenrollmentprofile-create?view=graph-rest-beta) | [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta) | Create a new [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta) object. |
| [Delete depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depenrollmentprofile-delete?view=graph-rest-beta) | None | Deletes a [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta). |
| [Update depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depenrollmentprofile-update?view=graph-rest-beta) | [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta) | Update the properties of a [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta) object. |

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
| isDefault | Boolean | Indicates if this is the default profile |
| supervisedModeEnabled | Boolean | Supervised mode, True to enable, false otherwise. See [https://learn.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune](https://learn.microsoft.com/en-us/intune/deploy-use/enroll-devices-in-microsoft-intune) for additional information. |
| supportDepartment | String | Support department information |
| passCodeDisabled | Boolean | Indicates if Passcode setup pane is disabled |
| isMandatory | Boolean | Indicates if the profile is mandatory |
| locationDisabled | Boolean | Indicates if Location service setup pane is disabled |
| supportPhoneNumber | String | Support phone number |
| iTunesPairingMode | [iTunesPairingMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-itunespairingmode?view=graph-rest-beta) | Indicates the iTunes pairing mode. Possible values are: `disallow`, `allow`, `requiresCertificate`. |
| profileRemovalDisabled | Boolean | Indicates if the profile removal option is disabled |
| managementCertificates | [managementCertificateWithThumbprint](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-managementcertificatewiththumbprint?view=graph-rest-beta) collection | Management certificates for Apple Configurator |
| restoreBlocked | Boolean | Indicates if Restore setup pane is blocked |
| restoreFromAndroidDisabled | Boolean | Indicates if Restore from Android is disabled |
| appleIdDisabled | Boolean | Indicates if Apple id setup pane is disabled |
| termsAndConditionsDisabled | Boolean | Indicates if 'Terms and Conditions' setup pane is disabled |
| touchIdDisabled | Boolean | Indicates if touch id setup pane is disabled |
| applePayDisabled | Boolean | Indicates if Apple pay setup pane is disabled |
| zoomDisabled | Boolean | Indicates if zoom setup pane is disabled |
| siriDisabled | Boolean | Indicates if siri setup pane is disabled |
| diagnosticsDisabled | Boolean | Indicates if diagnostics setup pane is disabled |
| macOSRegistrationDisabled | Boolean | Indicates if Mac OS registration is disabled |
| macOSFileVaultDisabled | Boolean | Indicates if Mac OS file vault is disabled |
| awaitDeviceConfiguredConfirmation | Boolean | Indicates if the device will need to wait for configured confirmation |
| sharedIPadMaximumUserCount | Int32 | This specifies the maximum number of users that can use a shared iPad. Only applicable in shared iPad mode. |
| enableSharedIPad | Boolean | This indicates whether the device is to be enrolled in a mode which enables multi user scenarios. Only applicable in shared iPads. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.depEnrollmentProfile",
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
  "passCodeDisabled": true,
  "isMandatory": true,
  "locationDisabled": true,
  "supportPhoneNumber": "String",
  "iTunesPairingMode": "String",
  "profileRemovalDisabled": true,
  "managementCertificates": [
    {
      "@odata.type": "microsoft.graph.managementCertificateWithThumbprint",
      "thumbprint": "String",
      "certificate": "String"
    }
  ],
  "restoreBlocked": true,
  "restoreFromAndroidDisabled": true,
  "appleIdDisabled": true,
  "termsAndConditionsDisabled": true,
  "touchIdDisabled": true,
  "applePayDisabled": true,
  "zoomDisabled": true,
  "siriDisabled": true,
  "diagnosticsDisabled": true,
  "macOSRegistrationDisabled": true,
  "macOSFileVaultDisabled": true,
  "awaitDeviceConfiguredConfirmation": true,
  "sharedIPadMaximumUserCount": 1024,
  "enableSharedIPad": true
}
```
