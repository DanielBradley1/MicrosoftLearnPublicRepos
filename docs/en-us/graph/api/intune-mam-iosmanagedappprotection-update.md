<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-mam-iosmanagedappprotection-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Update iosManagedAppProtection

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceAppManagement/iosManagedAppProtections/{iosManagedAppProtectionId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Policy display name. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| description | String | The policy's description. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | The date and time the policy was created. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | Last time the policy was modified. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| id | String | Key of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| version | String | Version of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| periodOfflineBeforeAccessCheck | Duration | The period after which access is checked when the device is not connected to the internet. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| periodOnlineBeforeAccessCheck | Duration | The period after which access is checked when the device is connected to the internet. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| allowedInboundDataTransferSources | [managedAppDataTransferLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdatatransferlevel?view=graph-rest-1.0) | Sources from which data is allowed to be transferred. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0). The possible values are: `allApps`, `managedApps`, `none`. |
| allowedOutboundDataTransferDestinations | [managedAppDataTransferLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdatatransferlevel?view=graph-rest-1.0) | Destinations to which data is allowed to be transferred. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0). The possible values are: `allApps`, `managedApps`, `none`. |
| organizationalCredentialsRequired | Boolean | Indicates whether organizational credentials are required for app use. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| allowedOutboundClipboardSharingLevel | [managedAppClipboardSharingLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappclipboardsharinglevel?view=graph-rest-1.0) | The level to which the clipboard may be shared between apps on the managed device. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0). The possible values are: `allApps`, `managedAppsWithPasteIn`, `managedApps`, `blocked`. |
| dataBackupBlocked | Boolean | Indicates whether the backup of a managed app's data is blocked. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| deviceComplianceRequired | Boolean | Indicates whether device compliance is required. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| managedBrowserToOpenLinksRequired | Boolean | Indicates whether internet links should be opened in the managed browser app, or any custom browser specified by CustomBrowserProtocol \(for iOS\) or CustomBrowserPackageId/CustomBrowserDisplayName \(for Android\) Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| saveAsBlocked | Boolean | Indicates whether users may use the "Save As" menu item to save a copy of protected files. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| periodOfflineBeforeWipeIsEnforced | Duration | The amount of time an app is allowed to remain disconnected from the internet before all managed data it is wiped. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| pinRequired | Boolean | Indicates whether an app-level pin is required. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| maximumPinRetries | Int32 | Maximum number of incorrect pin retry attempts before the managed app is either blocked or wiped. Valid values 1 to 65535 Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| simplePinBlocked | Boolean | Indicates whether simplePin is blocked. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| minimumPinLength | Int32 | Minimum pin length required for an app-level pin if PinRequired is set to True Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| pinCharacterSet | [managedAppPinCharacterSet](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppincharacterset?view=graph-rest-1.0) | Character set which may be used for an app-level pin if PinRequired is set to True. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0). The possible values are: `numeric`, `alphanumericAndSymbol`. |
| periodBeforePinReset | Duration | TimePeriod before the all-level pin must be reset if PinRequired is set to True. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| allowedDataStorageLocations | [managedAppDataStorageLocation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdatastoragelocation?view=graph-rest-1.0) collection | Data storage locations where a user may store managed data. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0). The possible values are: `oneDriveForBusiness`, `sharePoint`, `box`, `localStorage`. |
| contactSyncBlocked | Boolean | Indicates whether contacts can be synced to the user's device. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| printBlocked | Boolean | Indicates whether printing is allowed from managed apps. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| fingerprintBlocked | Boolean | Indicates whether use of the fingerprint reader is allowed in place of a pin if PinRequired is set to True. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| disableAppPinIfDevicePinIsSet | Boolean | Indicates whether use of the app pin is required if the device pin is set. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| minimumRequiredOsVersion | String | Versions less than the specified version will block the managed app from accessing company data. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| minimumWarningOsVersion | String | Versions less than the specified version will result in warning message on the managed app from accessing company data. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| minimumRequiredAppVersion | String | Versions less than the specified version will block the managed app from accessing company data. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| minimumWarningAppVersion | String | Versions less than the specified version will result in warning message on the managed app. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
| managedBrowser | [managedBrowserType](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedbrowsertype?view=graph-rest-1.0) | Indicates in which managed browser\(s\) that internet links should be opened. When this property is configured, ManagedBrowserToOpenLinksRequired should be true. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0). The possible values are: `notConfigured`, `microsoftEdge`. |
| isAssigned | Boolean | Indicates if the policy is deployed to any inclusion groups or not. Inherited from [targetedManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappprotection?view=graph-rest-1.0) |
| appDataEncryptionType | [managedAppDataEncryptionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdataencryptiontype?view=graph-rest-1.0) | Type of encryption which should be used for data in a managed app. The possible values are: `useDeviceSettings`, `afterDeviceRestart`, `whenDeviceLockedExceptOpenFiles`, `whenDeviceLocked`. |
| minimumRequiredSdkVersion | String | Versions less than the specified version will block the managed app from accessing company data. |
| deployedAppCount | Int32 | Count of apps to which the current policy is deployed. |
| faceIdBlocked | Boolean | Indicates whether use of the FaceID is allowed in place of a pin if PinRequired is set to True. |
| customBrowserProtocol | String | A custom browser protocol to open weblink on iOS. When this property is configured, ManagedBrowserToOpenLinksRequired should be true. |

## Response

If successful, this method returns a `200 OK` response code and an updated [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceAppManagement/iosManagedAppProtections/{iosManagedAppProtectionId}
Content-type: application/json
Content-length: 1667

{
  "@odata.type": "#microsoft.graph.iosManagedAppProtection",
  "displayName": "Display Name value",
  "description": "Description value",
  "version": "Version value",
  "periodOfflineBeforeAccessCheck": "-PT17.1357909S",
  "periodOnlineBeforeAccessCheck": "PT35.0018757S",
  "allowedInboundDataTransferSources": "managedApps",
  "allowedOutboundDataTransferDestinations": "managedApps",
  "organizationalCredentialsRequired": true,
  "allowedOutboundClipboardSharingLevel": "managedAppsWithPasteIn",
  "dataBackupBlocked": true,
  "deviceComplianceRequired": true,
  "managedBrowserToOpenLinksRequired": true,
  "saveAsBlocked": true,
  "periodOfflineBeforeWipeIsEnforced": "-PT3M22.1587532S",
  "pinRequired": true,
  "maximumPinRetries": 1,
  "simplePinBlocked": true,
  "minimumPinLength": 0,
  "pinCharacterSet": "alphanumericAndSymbol",
  "periodBeforePinReset": "PT3M29.6631862S",
  "allowedDataStorageLocations": [
    "sharePoint"
  ],
  "contactSyncBlocked": true,
  "printBlocked": true,
  "fingerprintBlocked": true,
  "disableAppPinIfDevicePinIsSet": true,
  "minimumRequiredOsVersion": "Minimum Required Os Version value",
  "minimumWarningOsVersion": "Minimum Warning Os Version value",
  "minimumRequiredAppVersion": "Minimum Required App Version value",
  "minimumWarningAppVersion": "Minimum Warning App Version value",
  "managedBrowser": "microsoftEdge",
  "isAssigned": true,
  "appDataEncryptionType": "afterDeviceRestart",
  "minimumRequiredSdkVersion": "Minimum Required Sdk Version value",
  "deployedAppCount": 0,
  "faceIdBlocked": true,
  "customBrowserProtocol": "Custom Browser Protocol value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1839

{
  "@odata.type": "#microsoft.graph.iosManagedAppProtection",
  "displayName": "Display Name value",
  "description": "Description value",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "id": "5bc789cb-89cb-5bc7-cb89-c75bcb89c75b",
  "version": "Version value",
  "periodOfflineBeforeAccessCheck": "-PT17.1357909S",
  "periodOnlineBeforeAccessCheck": "PT35.0018757S",
  "allowedInboundDataTransferSources": "managedApps",
  "allowedOutboundDataTransferDestinations": "managedApps",
  "organizationalCredentialsRequired": true,
  "allowedOutboundClipboardSharingLevel": "managedAppsWithPasteIn",
  "dataBackupBlocked": true,
  "deviceComplianceRequired": true,
  "managedBrowserToOpenLinksRequired": true,
  "saveAsBlocked": true,
  "periodOfflineBeforeWipeIsEnforced": "-PT3M22.1587532S",
  "pinRequired": true,
  "maximumPinRetries": 1,
  "simplePinBlocked": true,
  "minimumPinLength": 0,
  "pinCharacterSet": "alphanumericAndSymbol",
  "periodBeforePinReset": "PT3M29.6631862S",
  "allowedDataStorageLocations": [
    "sharePoint"
  ],
  "contactSyncBlocked": true,
  "printBlocked": true,
  "fingerprintBlocked": true,
  "disableAppPinIfDevicePinIsSet": true,
  "minimumRequiredOsVersion": "Minimum Required Os Version value",
  "minimumWarningOsVersion": "Minimum Warning Os Version value",
  "minimumRequiredAppVersion": "Minimum Required App Version value",
  "minimumWarningAppVersion": "Minimum Warning App Version value",
  "managedBrowser": "microsoftEdge",
  "isAssigned": true,
  "appDataEncryptionType": "afterDeviceRestart",
  "minimumRequiredSdkVersion": "Minimum Required Sdk Version value",
  "deployedAppCount": 0,
  "faceIdBlocked": true,
  "customBrowserProtocol": "Custom Browser Protocol value"
}
```
