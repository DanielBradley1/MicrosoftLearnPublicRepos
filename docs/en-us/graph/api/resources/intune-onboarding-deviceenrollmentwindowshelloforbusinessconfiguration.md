<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# deviceEnrollmentWindowsHelloForBusinessConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Hello for Business settings lets users access their devices using a gesture, such as biometric authentication, or a PIN. Configure settings for enrolled Windows 10, Windows 10 Mobile and later.

Inherits from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceEnrollmentWindowsHelloForBusinessConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration-list?view=graph-rest-1.0) | [deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration?view=graph-rest-1.0) objects. |
| [Get deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration-get?view=graph-rest-1.0) | [deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration?view=graph-rest-1.0) object. |
| [Create deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration-create?view=graph-rest-1.0) | [deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration?view=graph-rest-1.0) | Create a new [deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration?view=graph-rest-1.0) object. |
| [Delete deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration?view=graph-rest-1.0). |
| [Update deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration-update?view=graph-rest-1.0) | [deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration?view=graph-rest-1.0) | Update the properties of a [deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the account Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| displayName | String | The display name of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| description | String | The description of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| priority | Int32 | Priority is used when a user exists in multiple groups that are assigned enrollment configuration. Users are subject only to the configuration with the lowest priority value. Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | Created date time in UTC of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | Last modified date time in UTC of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| version | Int32 | The version of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| pinMinimumLength | Int32 | Controls the minimum number of characters required for the Windows Hello for Business PIN. This value must be between 4 and 127, inclusive, and less than or equal to the value set for the maximum PIN. |
| pinMaximumLength | Int32 | Controls the maximum number of characters allowed for the Windows Hello for Business PIN. This value must be between 4 and 127, inclusive. This value must be greater than or equal to the value set for the minimum PIN. |
| pinUppercaseCharactersUsage | [windowsHelloForBusinessPinUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowshelloforbusinesspinusage?view=graph-rest-1.0) | Controls the ability to use uppercase letters in the Windows Hello for Business PIN. Allowed permits the use of uppercase letter\(s\), whereas Required ensures they are present. If set to Not Allowed, uppercase letters will not be permitted. The possible values are: `allowed`, `required`, `disallowed`. |
| pinLowercaseCharactersUsage | [windowsHelloForBusinessPinUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowshelloforbusinesspinusage?view=graph-rest-1.0) | Controls the ability to use lowercase letters in the Windows Hello for Business PIN. Allowed permits the use of lowercase letter\(s\), whereas Required ensures they are present. If set to Not Allowed, lowercase letters will not be permitted. The possible values are: `allowed`, `required`, `disallowed`. |
| pinSpecialCharactersUsage | [windowsHelloForBusinessPinUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowshelloforbusinesspinusage?view=graph-rest-1.0) | Controls the ability to use special characters in the Windows Hello for Business PIN. Allowed permits the use of special character\(s\), whereas Required ensures they are present. If set to Not Allowed, special character\(s\) will not be permitted. The possible values are: `allowed`, `required`, `disallowed`. |
| state | [enablement](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enablement?view=graph-rest-1.0) | Controls whether to allow the device to be configured for Windows Hello for Business. If set to disabled, the user cannot provision Windows Hello for Business except on Azure Active Directory joined mobile phones if otherwise required. If set to Not Configured, Intune will not override client defaults. The possible values are: `notConfigured`, `enabled`, `disabled`. |
| securityDeviceRequired | Boolean | Controls whether to require a Trusted Platform Module \(TPM\) for provisioning Windows Hello for Business. A TPM provides an additional security benefit in that data stored on it cannot be used on other devices. If set to False, all devices can provision Windows Hello for Business even if there is not a usable TPM. |
| unlockWithBiometricsEnabled | Boolean | Controls the use of biometric gestures, such as face and fingerprint, as an alternative to the Windows Hello for Business PIN. If set to False, biometric gestures are not allowed. Users must still configure a PIN as a backup in case of failures. |
| remotePassportEnabled | Boolean | Controls the use of Remote Windows Hello for Business. Remote Windows Hello for Business provides the ability for a portable, registered device to be usable as a companion for desktop authentication. The desktop must be Azure AD joined and the companion device must have a Windows Hello for Business PIN. |
| pinPreviousBlockCount | Int32 | Controls the ability to prevent users from using past PINs. This must be set between 0 and 50, inclusive, and the current PIN of the user is included in that count. If set to 0, previous PINs are not stored. PIN history is not preserved through a PIN reset. |
| pinExpirationInDays | Int32 | Controls the period of time \(in days\) that a PIN can be used before the system requires the user to change it. This must be set between 0 and 730, inclusive. If set to 0, the user's PIN will never expire |
| enhancedBiometricsState | [enablement](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enablement?view=graph-rest-1.0) | Controls the ability to use the anti-spoofing features for facial recognition on devices which support it. If set to disabled, anti-spoofing features are not allowed. If set to Not Configured, the user can choose whether they want to use anti-spoofing. The possible values are: `notConfigured`, `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0) collection | The list of group assignments for the device configuration profile Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceEnrollmentWindowsHelloForBusinessConfiguration",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "priority": 1024,
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "version": 1024,
  "pinMinimumLength": 1024,
  "pinMaximumLength": 1024,
  "pinUppercaseCharactersUsage": "String",
  "pinLowercaseCharactersUsage": "String",
  "pinSpecialCharactersUsage": "String",
  "state": "String",
  "securityDeviceRequired": true,
  "unlockWithBiometricsEnabled": true,
  "remotePassportEnabled": true,
  "pinPreviousBlockCount": 1024,
  "pinExpirationInDays": 1024,
  "enhancedBiometricsState": "String"
}
```
