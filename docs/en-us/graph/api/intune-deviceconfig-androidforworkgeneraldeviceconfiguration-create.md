<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidforworkgeneraldeviceconfiguration-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# Create androidForWorkGeneralDeviceConfiguration

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta) object.

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
POST /deviceManagement/deviceConfigurations
POST /deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.windowsDomainJoinConfiguration/networkAccessConfigurations
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the androidForWorkGeneralDeviceConfiguration object.

The following table shows the properties that are required when you create the androidForWorkGeneralDeviceConfiguration.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| supportsScopeTags | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleOsEdition | [deviceManagementApplicabilityRuleOsEdition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruleosedition?view=graph-rest-beta) | The OS edition applicability for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleOsVersion | [deviceManagementApplicabilityRuleOsVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruleosversion?view=graph-rest-beta) | The OS version applicability rule for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleDeviceMode | [deviceManagementApplicabilityRuleDeviceMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruledevicemode?view=graph-rest-beta) | The device mode applicability rule for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| passwordBlockFaceUnlock | Boolean | Indicates whether or not to block face unlock. |
| passwordBlockFingerprintUnlock | Boolean | Indicates whether or not to block fingerprint unlock. |
| passwordBlockIrisUnlock | Boolean | Indicates whether or not to block iris unlock. |
| passwordBlockTrustAgents | Boolean | Indicates whether or not to block Smart Lock and other trust agents. |
| passwordExpirationDays | Int32 | Number of days before the password expires. Valid values 1 to 365 |
| passwordMinimumLength | Int32 | Minimum length of passwords. Valid values 4 to 16 |
| passwordMinutesOfInactivityBeforeScreenTimeout | Int32 | Minutes of inactivity before the screen times out. |
| passwordPreviousPasswordBlockCount | Int32 | Number of previous passwords to block. Valid values 0 to 24 |
| passwordSignInFailureCountBeforeFactoryReset | Int32 | Number of sign in failures allowed before factory reset. Valid values 1 to 16 |
| passwordRequiredType | [androidForWorkRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkrequiredpasswordtype?view=graph-rest-beta) | Type of password that is required. Possible values are: `deviceDefault`, `lowSecurityBiometric`, `required`, `atLeastNumeric`, `numericComplex`, `atLeastAlphabetic`, `atLeastAlphanumeric`, `alphanumericWithSymbols`. |
| requiredPasswordComplexity | [androidRequiredPasswordComplexity](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidrequiredpasswordcomplexity?view=graph-rest-beta) | Indicates the required device password complexity on Android. One of: NONE, LOW, MEDIUM, HIGH. This is a new API targeted to Android 12+. Possible values are: `none`, `low`, `medium`, `high`. |
| workProfileDataSharingType | [androidForWorkCrossProfileDataSharingType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkcrossprofiledatasharingtype?view=graph-rest-beta) | Type of data sharing that is allowed. Possible values are: `deviceDefault`, `preventAny`, `allowPersonalToWork`, `noRestrictions`. |
| workProfileBlockNotificationsWhileDeviceLocked | Boolean | Indicates whether or not to block notifications while device locked. |
| workProfileBlockAddingAccounts | Boolean | Block users from adding/removing accounts in work profile. |
| workProfileBluetoothEnableContactSharing | Boolean | Allow bluetooth devices to access enterprise contacts. |
| workProfileBlockScreenCapture | Boolean | Block screen capture in work profile. |
| workProfileBlockCrossProfileCallerId | Boolean | Block display work profile caller ID in personal profile. |
| workProfileBlockCamera | Boolean | Block work profile camera. |
| workProfileBlockCrossProfileContactsSearch | Boolean | Block work profile contacts availability in personal profile. |
| workProfileBlockCrossProfileCopyPaste | Boolean | Boolean that indicates if the setting disallow cross profile copy/paste is enabled. |
| workProfileDefaultAppPermissionPolicy | [androidForWorkDefaultAppPermissionPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkdefaultapppermissionpolicytype?view=graph-rest-beta) | Type of password that is required. Possible values are: `deviceDefault`, `prompt`, `autoGrant`, `autoDeny`. |
| workProfilePasswordBlockFaceUnlock | Boolean | Indicates whether or not to block face unlock for work profile. |
| workProfilePasswordBlockFingerprintUnlock | Boolean | Indicates whether or not to block fingerprint unlock for work profile. |
| workProfilePasswordBlockIrisUnlock | Boolean | Indicates whether or not to block iris unlock for work profile. |
| workProfilePasswordBlockTrustAgents | Boolean | Indicates whether or not to block Smart Lock and other trust agents for work profile. |
| workProfilePasswordExpirationDays | Int32 | Number of days before the work profile password expires. Valid values 1 to 365 |
| workProfilePasswordMinimumLength | Int32 | Minimum length of work profile password. Valid values 4 to 16 |
| workProfilePasswordMinNumericCharacters | Int32 | Minimum # of numeric characters required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinNonLetterCharacters | Int32 | Minimum # of non-letter characters required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinLetterCharacters | Int32 | Minimum # of letter characters required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinLowerCaseCharacters | Int32 | Minimum # of lower-case characters required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinUpperCaseCharacters | Int32 | Minimum # of upper-case characters required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinSymbolCharacters | Int32 | Minimum # of symbols required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinutesOfInactivityBeforeScreenTimeout | Int32 | Minutes of inactivity before the screen times out. |
| workProfilePasswordPreviousPasswordBlockCount | Int32 | Number of previous work profile passwords to block. Valid values 0 to 24 |
| workProfilePasswordSignInFailureCountBeforeFactoryReset | Int32 | Number of sign in failures allowed before work profile is removed and all corporate data deleted. Valid values 1 to 16 |
| workProfilePasswordRequiredType | [androidForWorkRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkrequiredpasswordtype?view=graph-rest-beta) | Type of work profile password that is required. Possible values are: `deviceDefault`, `lowSecurityBiometric`, `required`, `atLeastNumeric`, `numericComplex`, `atLeastAlphabetic`, `atLeastAlphanumeric`, `alphanumericWithSymbols`. |
| workProfileRequiredPasswordComplexity | [androidRequiredPasswordComplexity](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidrequiredpasswordcomplexity?view=graph-rest-beta) | Indicates the required work profile password complexity on Android. One of: NONE, LOW, MEDIUM, HIGH. This is a new API targeted to Android 12+. Possible values are: `none`, `low`, `medium`, `high`. |
| workProfileRequirePassword | Boolean | Password is required or not for work profile |
| securityRequireVerifyApps | Boolean | Require the Android Verify apps feature is turned on. |
| vpnAlwaysOnPackageIdentifier | String | Enable lockdown mode for always-on VPN. |
| vpnEnableAlwaysOnLockdownMode | Boolean | Enable lockdown mode for always-on VPN. |
| workProfileAllowWidgets | Boolean | Allow widgets from work profile apps. |
| workProfileBlockPersonalAppInstallsFromUnknownSources | Boolean | Prevent app installations from unknown sources in the personal profile. |
| workProfileAccountUse | [androidWorkProfileAccountUse](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileaccountuse?view=graph-rest-beta) | Control user's ability to add accounts in work profile including Google accounts. Possible values are: `allowAllExceptGoogleAccounts`, `blockAll`, `allowAll`, `unknownFutureValue`. |
| allowedGoogleAccountDomains | String collection | Determine domains allow-list for accounts that can be added to work profile. |
| blockUnifiedPasswordForWorkProfile | Boolean | Prevent using unified password for unlocking device and work profile. |

## Response

If successful, this method returns a `201 Created` response code and a [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations
Content-type: application/json
Content-length: 3343

{
  "@odata.type": "#microsoft.graph.androidForWorkGeneralDeviceConfiguration",
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "supportsScopeTags": true,
  "deviceManagementApplicabilityRuleOsEdition": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsEdition",
    "osEditionTypes": [
      "windows10EnterpriseN"
    ],
    "name": "Name value",
    "ruleType": "exclude"
  },
  "deviceManagementApplicabilityRuleOsVersion": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsVersion",
    "minOSVersion": "Min OSVersion value",
    "maxOSVersion": "Max OSVersion value",
    "name": "Name value",
    "ruleType": "exclude"
  },
  "deviceManagementApplicabilityRuleDeviceMode": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleDeviceMode",
    "deviceMode": "sModeConfiguration",
    "name": "Name value",
    "ruleType": "exclude"
  },
  "description": "Description value",
  "displayName": "Display Name value",
  "version": 7,
  "passwordBlockFaceUnlock": true,
  "passwordBlockFingerprintUnlock": true,
  "passwordBlockIrisUnlock": true,
  "passwordBlockTrustAgents": true,
  "passwordExpirationDays": 6,
  "passwordMinimumLength": 5,
  "passwordMinutesOfInactivityBeforeScreenTimeout": 14,
  "passwordPreviousPasswordBlockCount": 2,
  "passwordSignInFailureCountBeforeFactoryReset": 12,
  "passwordRequiredType": "lowSecurityBiometric",
  "requiredPasswordComplexity": "low",
  "workProfileDataSharingType": "preventAny",
  "workProfileBlockNotificationsWhileDeviceLocked": true,
  "workProfileBlockAddingAccounts": true,
  "workProfileBluetoothEnableContactSharing": true,
  "workProfileBlockScreenCapture": true,
  "workProfileBlockCrossProfileCallerId": true,
  "workProfileBlockCamera": true,
  "workProfileBlockCrossProfileContactsSearch": true,
  "workProfileBlockCrossProfileCopyPaste": true,
  "workProfileDefaultAppPermissionPolicy": "prompt",
  "workProfilePasswordBlockFaceUnlock": true,
  "workProfilePasswordBlockFingerprintUnlock": true,
  "workProfilePasswordBlockIrisUnlock": true,
  "workProfilePasswordBlockTrustAgents": true,
  "workProfilePasswordExpirationDays": 1,
  "workProfilePasswordMinimumLength": 0,
  "workProfilePasswordMinNumericCharacters": 7,
  "workProfilePasswordMinNonLetterCharacters": 9,
  "workProfilePasswordMinLetterCharacters": 6,
  "workProfilePasswordMinLowerCaseCharacters": 9,
  "workProfilePasswordMinUpperCaseCharacters": 9,
  "workProfilePasswordMinSymbolCharacters": 6,
  "workProfilePasswordMinutesOfInactivityBeforeScreenTimeout": 9,
  "workProfilePasswordPreviousPasswordBlockCount": 13,
  "workProfilePasswordSignInFailureCountBeforeFactoryReset": 7,
  "workProfilePasswordRequiredType": "lowSecurityBiometric",
  "workProfileRequiredPasswordComplexity": "low",
  "workProfileRequirePassword": true,
  "securityRequireVerifyApps": true,
  "vpnAlwaysOnPackageIdentifier": "Vpn Always On Package Identifier value",
  "vpnEnableAlwaysOnLockdownMode": true,
  "workProfileAllowWidgets": true,
  "workProfileBlockPersonalAppInstallsFromUnknownSources": true,
  "workProfileAccountUse": "blockAll",
  "allowedGoogleAccountDomains": [
    "Allowed Google Account Domains value"
  ],
  "blockUnifiedPasswordForWorkProfile": true
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 3515

{
  "@odata.type": "#microsoft.graph.androidForWorkGeneralDeviceConfiguration",
  "id": "a931a366-a366-a931-66a3-31a966a331a9",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "supportsScopeTags": true,
  "deviceManagementApplicabilityRuleOsEdition": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsEdition",
    "osEditionTypes": [
      "windows10EnterpriseN"
    ],
    "name": "Name value",
    "ruleType": "exclude"
  },
  "deviceManagementApplicabilityRuleOsVersion": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsVersion",
    "minOSVersion": "Min OSVersion value",
    "maxOSVersion": "Max OSVersion value",
    "name": "Name value",
    "ruleType": "exclude"
  },
  "deviceManagementApplicabilityRuleDeviceMode": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleDeviceMode",
    "deviceMode": "sModeConfiguration",
    "name": "Name value",
    "ruleType": "exclude"
  },
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "description": "Description value",
  "displayName": "Display Name value",
  "version": 7,
  "passwordBlockFaceUnlock": true,
  "passwordBlockFingerprintUnlock": true,
  "passwordBlockIrisUnlock": true,
  "passwordBlockTrustAgents": true,
  "passwordExpirationDays": 6,
  "passwordMinimumLength": 5,
  "passwordMinutesOfInactivityBeforeScreenTimeout": 14,
  "passwordPreviousPasswordBlockCount": 2,
  "passwordSignInFailureCountBeforeFactoryReset": 12,
  "passwordRequiredType": "lowSecurityBiometric",
  "requiredPasswordComplexity": "low",
  "workProfileDataSharingType": "preventAny",
  "workProfileBlockNotificationsWhileDeviceLocked": true,
  "workProfileBlockAddingAccounts": true,
  "workProfileBluetoothEnableContactSharing": true,
  "workProfileBlockScreenCapture": true,
  "workProfileBlockCrossProfileCallerId": true,
  "workProfileBlockCamera": true,
  "workProfileBlockCrossProfileContactsSearch": true,
  "workProfileBlockCrossProfileCopyPaste": true,
  "workProfileDefaultAppPermissionPolicy": "prompt",
  "workProfilePasswordBlockFaceUnlock": true,
  "workProfilePasswordBlockFingerprintUnlock": true,
  "workProfilePasswordBlockIrisUnlock": true,
  "workProfilePasswordBlockTrustAgents": true,
  "workProfilePasswordExpirationDays": 1,
  "workProfilePasswordMinimumLength": 0,
  "workProfilePasswordMinNumericCharacters": 7,
  "workProfilePasswordMinNonLetterCharacters": 9,
  "workProfilePasswordMinLetterCharacters": 6,
  "workProfilePasswordMinLowerCaseCharacters": 9,
  "workProfilePasswordMinUpperCaseCharacters": 9,
  "workProfilePasswordMinSymbolCharacters": 6,
  "workProfilePasswordMinutesOfInactivityBeforeScreenTimeout": 9,
  "workProfilePasswordPreviousPasswordBlockCount": 13,
  "workProfilePasswordSignInFailureCountBeforeFactoryReset": 7,
  "workProfilePasswordRequiredType": "lowSecurityBiometric",
  "workProfileRequiredPasswordComplexity": "low",
  "workProfileRequirePassword": true,
  "securityRequireVerifyApps": true,
  "vpnAlwaysOnPackageIdentifier": "Vpn Always On Package Identifier value",
  "vpnEnableAlwaysOnLockdownMode": true,
  "workProfileAllowWidgets": true,
  "workProfileBlockPersonalAppInstallsFromUnknownSources": true,
  "workProfileAccountUse": "blockAll",
  "allowedGoogleAccountDomains": [
    "Allowed Google Account Domains value"
  ],
  "blockUnifiedPasswordForWorkProfile": true
}
```
