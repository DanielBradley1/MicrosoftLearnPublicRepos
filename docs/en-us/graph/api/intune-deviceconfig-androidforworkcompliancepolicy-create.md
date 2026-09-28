<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidforworkcompliancepolicy-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create androidForWorkCompliancePolicy

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [androidForWorkCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkcompliancepolicy?view=graph-rest-beta) object.

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
POST /deviceManagement/deviceCompliancePolicies
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the androidForWorkCompliancePolicy object.

The following table shows the properties that are required when you create the androidForWorkCompliancePolicy.

| Property | Type | Description |
| :--- | :--- | :--- |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| version | Int32 | Version of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| passwordRequired | Boolean | Require a password to unlock device. |
| passwordMinimumLength | Int32 | Minimum password length. Valid values 4 to 16 |
| passwordRequiredType | [androidRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidrequiredpasswordtype?view=graph-rest-beta) | Type of characters in password. Possible values are: `deviceDefault`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `numeric`, `numericComplex`, `any`. |
| requiredPasswordComplexity | [androidRequiredPasswordComplexity](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidrequiredpasswordcomplexity?view=graph-rest-beta) | Indicates the required device password complexity on Android. One of: NONE, LOW, MEDIUM, HIGH. This is a new API targeted to Android API 12+. Possible values are: `none`, `low`, `medium`, `high`. |
| passwordMinutesOfInactivityBeforeLock | Int32 | Minutes of inactivity before a password is required. |
| passwordExpirationDays | Int32 | Number of days before the password expires. Valid values 1 to 365 |
| passwordPreviousPasswordBlockCount | Int32 | Number of previous passwords to block. Valid values 1 to 24 |
| passwordSignInFailureCountBeforeFactoryReset | Int32 | Number of sign-in failures allowed before factory reset. Valid values 1 to 16 |
| workProfilePasswordExpirationInDays | Int32 | Number of days before the work profile password expires. Valid values 1 to 365 |
| workProfilePasswordMinimumLength | Int32 | Minimum length of work profile password. Valid values 4 to 16 |
| workProfileInactiveBeforeScreenLockInMinutes | Int32 | Minutes of inactivity before the screen times out. |
| workProfilePreviousPasswordBlockCount | Int32 | Number of previous work profile passwords to block. Valid values 0 to 24 |
| workProfilePasswordRequiredType | [androidForWorkRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkrequiredpasswordtype?view=graph-rest-beta) | Type of work profile password that is required. Possible values are: `deviceDefault`, `lowSecurityBiometric`, `required`, `atLeastNumeric`, `numericComplex`, `atLeastAlphabetic`, `atLeastAlphanumeric`, `alphanumericWithSymbols`. |
| workProfileRequiredPasswordComplexity | [androidRequiredPasswordComplexity](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidrequiredpasswordcomplexity?view=graph-rest-beta) | Indicates the required work profile password complexity on Android. One of: NONE, LOW, MEDIUM, HIGH. This is a new API targeted to Android 12+. Possible values are: `none`, `low`, `medium`, `high`. |
| workProfileRequirePassword | Boolean | Password is required or not for work profile |
| securityPreventInstallAppsFromUnknownSources | Boolean | Require that devices disallow installation of apps from unknown sources. |
| securityDisableUsbDebugging | Boolean | Disable USB debugging on Android devices. |
| securityRequireVerifyApps | Boolean | Require the Android Verify apps feature is turned on. |
| deviceThreatProtectionEnabled | Boolean | Require that devices have enabled device threat protection. |
| deviceThreatProtectionRequiredSecurityLevel | [deviceThreatProtectionLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicethreatprotectionlevel?view=graph-rest-beta) | Require Mobile Threat Protection minimum risk level to report noncompliance. Possible values are: `unavailable`, `secured`, `low`, `medium`, `high`, `notSet`. |
| securityBlockJailbrokenDevices | Boolean | Indicates the device should not be rooted. When TRUE, if the device is detected as rooted it will be reported non-compliant. When FALSE, the device is not reported as non-compliant regardless of device rooted state. Default is FALSE. |
| osMinimumVersion | String | Minimum Android version. |
| osMaximumVersion | String | Maximum Android version. |
| minAndroidSecurityPatchLevel | String | Minimum Android security patch level. |
| storageRequireEncryption | Boolean | Require encryption on Android devices. |
| securityRequireSafetyNetAttestationBasicIntegrity | Boolean | Require the device to pass the Play Integrity basic integrity check. |
| securityRequireSafetyNetAttestationCertifiedDevice | Boolean | Require the device to pass the Play Integrity device integrity check. |
| securityRequireGooglePlayServices | Boolean | Require Google Play Services to be installed and enabled on the device. |
| securityRequireUpToDateSecurityProviders | Boolean | Require the device to have up to date security providers. The device will require Google Play Services to be enabled and up to date. |
| securityRequireCompanyPortalAppIntegrity | Boolean | Require the device to pass the Company Portal client app runtime integrity check. |
| securityRequiredAndroidSafetyNetEvaluationType | [androidSafetyNetEvaluationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidsafetynetevaluationtype?view=graph-rest-beta) | Require a specific SafetyNet evaluation type for compliance. Possible values are: `basic`, `hardwareBacked`. |

## Response

If successful, this method returns a `201 Created` response code and a [androidForWorkCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkcompliancepolicy?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/deviceCompliancePolicies
Content-type: application/json
Content-length: 1735

{
  "@odata.type": "#microsoft.graph.androidForWorkCompliancePolicy",
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "description": "Description value",
  "displayName": "Display Name value",
  "version": 7,
  "passwordRequired": true,
  "passwordMinimumLength": 5,
  "passwordRequiredType": "alphabetic",
  "requiredPasswordComplexity": "low",
  "passwordMinutesOfInactivityBeforeLock": 5,
  "passwordExpirationDays": 6,
  "passwordPreviousPasswordBlockCount": 2,
  "passwordSignInFailureCountBeforeFactoryReset": 12,
  "workProfilePasswordExpirationInDays": 3,
  "workProfilePasswordMinimumLength": 0,
  "workProfileInactiveBeforeScreenLockInMinutes": 12,
  "workProfilePreviousPasswordBlockCount": 5,
  "workProfilePasswordRequiredType": "lowSecurityBiometric",
  "workProfileRequiredPasswordComplexity": "low",
  "workProfileRequirePassword": true,
  "securityPreventInstallAppsFromUnknownSources": true,
  "securityDisableUsbDebugging": true,
  "securityRequireVerifyApps": true,
  "deviceThreatProtectionEnabled": true,
  "deviceThreatProtectionRequiredSecurityLevel": "secured",
  "securityBlockJailbrokenDevices": true,
  "osMinimumVersion": "Os Minimum Version value",
  "osMaximumVersion": "Os Maximum Version value",
  "minAndroidSecurityPatchLevel": "Min Android Security Patch Level value",
  "storageRequireEncryption": true,
  "securityRequireSafetyNetAttestationBasicIntegrity": true,
  "securityRequireSafetyNetAttestationCertifiedDevice": true,
  "securityRequireGooglePlayServices": true,
  "securityRequireUpToDateSecurityProviders": true,
  "securityRequireCompanyPortalAppIntegrity": true,
  "securityRequiredAndroidSafetyNetEvaluationType": "hardwareBacked"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 1907

{
  "@odata.type": "#microsoft.graph.androidForWorkCompliancePolicy",
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "id": "a8d667bd-67bd-a8d6-bd67-d6a8bd67d6a8",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "description": "Description value",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "displayName": "Display Name value",
  "version": 7,
  "passwordRequired": true,
  "passwordMinimumLength": 5,
  "passwordRequiredType": "alphabetic",
  "requiredPasswordComplexity": "low",
  "passwordMinutesOfInactivityBeforeLock": 5,
  "passwordExpirationDays": 6,
  "passwordPreviousPasswordBlockCount": 2,
  "passwordSignInFailureCountBeforeFactoryReset": 12,
  "workProfilePasswordExpirationInDays": 3,
  "workProfilePasswordMinimumLength": 0,
  "workProfileInactiveBeforeScreenLockInMinutes": 12,
  "workProfilePreviousPasswordBlockCount": 5,
  "workProfilePasswordRequiredType": "lowSecurityBiometric",
  "workProfileRequiredPasswordComplexity": "low",
  "workProfileRequirePassword": true,
  "securityPreventInstallAppsFromUnknownSources": true,
  "securityDisableUsbDebugging": true,
  "securityRequireVerifyApps": true,
  "deviceThreatProtectionEnabled": true,
  "deviceThreatProtectionRequiredSecurityLevel": "secured",
  "securityBlockJailbrokenDevices": true,
  "osMinimumVersion": "Os Minimum Version value",
  "osMaximumVersion": "Os Maximum Version value",
  "minAndroidSecurityPatchLevel": "Min Android Security Patch Level value",
  "storageRequireEncryption": true,
  "securityRequireSafetyNetAttestationBasicIntegrity": true,
  "securityRequireSafetyNetAttestationCertifiedDevice": true,
  "securityRequireGooglePlayServices": true,
  "securityRequireUpToDateSecurityProviders": true,
  "securityRequireCompanyPortalAppIntegrity": true,
  "securityRequiredAndroidSafetyNetEvaluationType": "hardwareBacked"
}
```
