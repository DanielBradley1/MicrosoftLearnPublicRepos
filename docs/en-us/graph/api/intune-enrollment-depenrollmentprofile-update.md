<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depenrollmentprofile-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Update depEnrollmentProfile

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta) object.

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
PATCH /deviceManagement/depOnboardingSettings/{depOnboardingSettingId}/enrollmentProfiles/{enrollmentProfileId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta).

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

## Response

If successful, this method returns a `200 OK` response code and an updated [depEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depenrollmentprofile?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/depOnboardingSettings/{depOnboardingSettingId}/enrollmentProfiles/{enrollmentProfileId}
Content-type: application/json
Content-length: 1354

{
  "@odata.type": "#microsoft.graph.depEnrollmentProfile",
  "displayName": "Display Name value",
  "description": "Description value",
  "requiresUserAuthentication": true,
  "configurationEndpointUrl": "https://example.com/configurationEndpointUrl/",
  "enableAuthenticationViaCompanyPortal": true,
  "requireCompanyPortalOnSetupAssistantEnrolledDevices": true,
  "isDefault": true,
  "supervisedModeEnabled": true,
  "supportDepartment": "Support Department value",
  "passCodeDisabled": true,
  "isMandatory": true,
  "locationDisabled": true,
  "supportPhoneNumber": "Support Phone Number value",
  "iTunesPairingMode": "allow",
  "profileRemovalDisabled": true,
  "managementCertificates": [
    {
      "@odata.type": "microsoft.graph.managementCertificateWithThumbprint",
      "thumbprint": "Thumbprint value",
      "certificate": "Certificate value"
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
  "sharedIPadMaximumUserCount": 10,
  "enableSharedIPad": true
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1403

{
  "@odata.type": "#microsoft.graph.depEnrollmentProfile",
  "id": "3d4534f7-34f7-3d45-f734-453df734453d",
  "displayName": "Display Name value",
  "description": "Description value",
  "requiresUserAuthentication": true,
  "configurationEndpointUrl": "https://example.com/configurationEndpointUrl/",
  "enableAuthenticationViaCompanyPortal": true,
  "requireCompanyPortalOnSetupAssistantEnrolledDevices": true,
  "isDefault": true,
  "supervisedModeEnabled": true,
  "supportDepartment": "Support Department value",
  "passCodeDisabled": true,
  "isMandatory": true,
  "locationDisabled": true,
  "supportPhoneNumber": "Support Phone Number value",
  "iTunesPairingMode": "allow",
  "profileRemovalDisabled": true,
  "managementCertificates": [
    {
      "@odata.type": "microsoft.graph.managementCertificateWithThumbprint",
      "thumbprint": "Thumbprint value",
      "certificate": "Certificate value"
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
  "sharedIPadMaximumUserCount": 10,
  "enableSharedIPad": true
}
```
