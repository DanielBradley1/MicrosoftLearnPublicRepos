<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows81generalconfiguration-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Update windows81GeneralConfiguration

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0) object.

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
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| accountsBlockAddingNonMicrosoftAccountEmail | Boolean | Indicates whether or not to Block the user from adding email accounts to the device that are not associated with a Microsoft account. |
| applyOnlyToWindows81 | Boolean | Value indicating whether this policy only applies to Windows 8.1. This property is read-only. |
| browserBlockAutofill | Boolean | Indicates whether or not to block auto fill. |
| browserBlockAutomaticDetectionOfIntranetSites | Boolean | Indicates whether or not to block automatic detection of Intranet sites. |
| browserBlockEnterpriseModeAccess | Boolean | Indicates whether or not to block enterprise mode access. |
| browserBlockJavaScript | Boolean | Indicates whether or not to Block the user from using JavaScript. |
| browserBlockPlugins | Boolean | Indicates whether or not to block plug-ins. |
| browserBlockPopups | Boolean | Indicates whether or not to block popups. |
| browserBlockSendingDoNotTrackHeader | Boolean | Indicates whether or not to Block the user from sending the do not track header. |
| browserBlockSingleWordEntryOnIntranetSites | Boolean | Indicates whether or not to block a single word entry on Intranet sites. |
| browserRequireSmartScreen | Boolean | Indicates whether or not to require the user to use the smart screen filter. |
| browserEnterpriseModeSiteListLocation | String | The enterprise mode site list location. Could be a local file, local network or http location. |
| browserInternetSecurityLevel | [internetSiteSecurityLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-internetsitesecuritylevel?view=graph-rest-1.0) | The internet security level. The possible values are: `userDefined`, `medium`, `mediumHigh`, `high`. |
| browserIntranetSecurityLevel | [siteSecurityLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sitesecuritylevel?view=graph-rest-1.0) | The Intranet security level. The possible values are: `userDefined`, `low`, `mediumLow`, `medium`, `mediumHigh`, `high`. |
| browserLoggingReportLocation | String | The logging report location. |
| browserRequireHighSecurityForRestrictedSites | Boolean | Indicates whether or not to require high security for restricted sites. |
| browserRequireFirewall | Boolean | Indicates whether or not to require a firewall. |
| browserRequireFraudWarning | Boolean | Indicates whether or not to require fraud warning. |
| browserTrustedSitesSecurityLevel | [siteSecurityLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sitesecuritylevel?view=graph-rest-1.0) | The trusted sites security level. The possible values are: `userDefined`, `low`, `mediumLow`, `medium`, `mediumHigh`, `high`. |
| cellularBlockDataRoaming | Boolean | Indicates whether or not to block data roaming. |
| diagnosticsBlockDataSubmission | Boolean | Indicates whether or not to block diagnostic data submission. |
| passwordBlockPicturePasswordAndPin | Boolean | Indicates whether or not to Block the user from using a pictures password and pin. |
| passwordExpirationDays | Int32 | Password expiration in days. |
| passwordMinimumLength | Int32 | The minimum password length. |
| passwordMinutesOfInactivityBeforeScreenTimeout | Int32 | The minutes of inactivity before the screen times out. |
| passwordMinimumCharacterSetCount | Int32 | The number of character sets required in the password. |
| passwordPreviousPasswordBlockCount | Int32 | The number of previous passwords to prevent re-use of. Valid values 0 to 24 |
| passwordRequiredType | [requiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-requiredpasswordtype?view=graph-rest-1.0) | The required password type. The possible values are: `deviceDefault`, `alphanumeric`, `numeric`. |
| passwordSignInFailureCountBeforeFactoryReset | Int32 | The number of sign in failures before factory reset. |
| storageRequireDeviceEncryption | Boolean | Indicates whether or not to require encryption on a mobile device. |
| updatesRequireAutomaticUpdates | Boolean | Indicates whether or not to require automatic updates. |
| userAccountControlSettings | [windowsUserAccountControlSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsuseraccountcontrolsettings?view=graph-rest-1.0) | The user account control settings. The possible values are: `userDefined`, `alwaysNotify`, `notifyOnAppChanges`, `notifyOnAppChangesWithoutDimming`, `neverNotify`. |
| workFoldersUrl | String | The work folders url. |

## Response

If successful, this method returns a `200 OK` response code and an updated [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceManagement/deviceConfigurations/{deviceConfigurationId}
Content-type: application/json
Content-length: 1693

{
  "@odata.type": "#microsoft.graph.windows81GeneralConfiguration",
  "description": "Description value",
  "displayName": "Display Name value",
  "version": 7,
  "accountsBlockAddingNonMicrosoftAccountEmail": true,
  "applyOnlyToWindows81": true,
  "browserBlockAutofill": true,
  "browserBlockAutomaticDetectionOfIntranetSites": true,
  "browserBlockEnterpriseModeAccess": true,
  "browserBlockJavaScript": true,
  "browserBlockPlugins": true,
  "browserBlockPopups": true,
  "browserBlockSendingDoNotTrackHeader": true,
  "browserBlockSingleWordEntryOnIntranetSites": true,
  "browserRequireSmartScreen": true,
  "browserEnterpriseModeSiteListLocation": "Browser Enterprise Mode Site List Location value",
  "browserInternetSecurityLevel": "medium",
  "browserIntranetSecurityLevel": "low",
  "browserLoggingReportLocation": "Browser Logging Report Location value",
  "browserRequireHighSecurityForRestrictedSites": true,
  "browserRequireFirewall": true,
  "browserRequireFraudWarning": true,
  "browserTrustedSitesSecurityLevel": "low",
  "cellularBlockDataRoaming": true,
  "diagnosticsBlockDataSubmission": true,
  "passwordBlockPicturePasswordAndPin": true,
  "passwordExpirationDays": 6,
  "passwordMinimumLength": 5,
  "passwordMinutesOfInactivityBeforeScreenTimeout": 14,
  "passwordMinimumCharacterSetCount": 0,
  "passwordPreviousPasswordBlockCount": 2,
  "passwordRequiredType": "alphanumeric",
  "passwordSignInFailureCountBeforeFactoryReset": 12,
  "storageRequireDeviceEncryption": true,
  "updatesRequireAutomaticUpdates": true,
  "userAccountControlSettings": "alwaysNotify",
  "workFoldersUrl": "https://example.com/workFoldersUrl/"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1865

{
  "@odata.type": "#microsoft.graph.windows81GeneralConfiguration",
  "id": "0e9285b5-85b5-0e92-b585-920eb585920e",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "description": "Description value",
  "displayName": "Display Name value",
  "version": 7,
  "accountsBlockAddingNonMicrosoftAccountEmail": true,
  "applyOnlyToWindows81": true,
  "browserBlockAutofill": true,
  "browserBlockAutomaticDetectionOfIntranetSites": true,
  "browserBlockEnterpriseModeAccess": true,
  "browserBlockJavaScript": true,
  "browserBlockPlugins": true,
  "browserBlockPopups": true,
  "browserBlockSendingDoNotTrackHeader": true,
  "browserBlockSingleWordEntryOnIntranetSites": true,
  "browserRequireSmartScreen": true,
  "browserEnterpriseModeSiteListLocation": "Browser Enterprise Mode Site List Location value",
  "browserInternetSecurityLevel": "medium",
  "browserIntranetSecurityLevel": "low",
  "browserLoggingReportLocation": "Browser Logging Report Location value",
  "browserRequireHighSecurityForRestrictedSites": true,
  "browserRequireFirewall": true,
  "browserRequireFraudWarning": true,
  "browserTrustedSitesSecurityLevel": "low",
  "cellularBlockDataRoaming": true,
  "diagnosticsBlockDataSubmission": true,
  "passwordBlockPicturePasswordAndPin": true,
  "passwordExpirationDays": 6,
  "passwordMinimumLength": 5,
  "passwordMinutesOfInactivityBeforeScreenTimeout": 14,
  "passwordMinimumCharacterSetCount": 0,
  "passwordPreviousPasswordBlockCount": 2,
  "passwordRequiredType": "alphanumeric",
  "passwordSignInFailureCountBeforeFactoryReset": 12,
  "storageRequireDeviceEncryption": true,
  "updatesRequireAutomaticUpdates": true,
  "userAccountControlSettings": "alwaysNotify",
  "workFoldersUrl": "https://example.com/workFoldersUrl/"
}
```
