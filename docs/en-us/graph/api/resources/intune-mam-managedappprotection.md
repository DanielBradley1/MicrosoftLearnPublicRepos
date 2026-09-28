<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# managedAppProtection resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Policy used to configure detailed management settings for a specified set of apps

Inherits from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedAppProtections](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappprotection-list?view=graph-rest-1.0) | [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) collection | List properties and relationships of the [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) objects. |
| [Get managedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappprotection-get?view=graph-rest-1.0) | [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) | Read properties and relationships of the [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) object. |
| [targetApps action](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappprotection-targetapps?view=graph-rest-1.0) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Policy display name. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| description | String | The policy's description. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | The date and time the policy was created. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | Last time the policy was modified. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| id | String | Key of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| version | String | Version of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| periodOfflineBeforeAccessCheck | Duration | The period after which access is checked when the device is not connected to the internet. |
| periodOnlineBeforeAccessCheck | Duration | The period after which access is checked when the device is connected to the internet. |
| allowedInboundDataTransferSources | [managedAppDataTransferLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdatatransferlevel?view=graph-rest-1.0) | Sources from which data is allowed to be transferred. The possible values are: `allApps`, `managedApps`, `none`. |
| allowedOutboundDataTransferDestinations | [managedAppDataTransferLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdatatransferlevel?view=graph-rest-1.0) | Destinations to which data is allowed to be transferred. The possible values are: `allApps`, `managedApps`, `none`. |
| organizationalCredentialsRequired | Boolean | Indicates whether organizational credentials are required for app use. |
| allowedOutboundClipboardSharingLevel | [managedAppClipboardSharingLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappclipboardsharinglevel?view=graph-rest-1.0) | The level to which the clipboard may be shared between apps on the managed device. The possible values are: `allApps`, `managedAppsWithPasteIn`, `managedApps`, `blocked`. |
| dataBackupBlocked | Boolean | Indicates whether the backup of a managed app's data is blocked. |
| deviceComplianceRequired | Boolean | Indicates whether device compliance is required. |
| managedBrowserToOpenLinksRequired | Boolean | Indicates whether internet links should be opened in the managed browser app, or any custom browser specified by CustomBrowserProtocol \(for iOS\) or CustomBrowserPackageId/CustomBrowserDisplayName \(for Android\) |
| saveAsBlocked | Boolean | Indicates whether users may use the "Save As" menu item to save a copy of protected files. |
| periodOfflineBeforeWipeIsEnforced | Duration | The amount of time an app is allowed to remain disconnected from the internet before all managed data it is wiped. |
| pinRequired | Boolean | Indicates whether an app-level pin is required. |
| maximumPinRetries | Int32 | Maximum number of incorrect pin retry attempts before the managed app is either blocked or wiped. Valid values 1 to 65535 |
| simplePinBlocked | Boolean | Indicates whether simplePin is blocked. |
| minimumPinLength | Int32 | Minimum pin length required for an app-level pin if PinRequired is set to True |
| pinCharacterSet | [managedAppPinCharacterSet](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppincharacterset?view=graph-rest-1.0) | Character set which may be used for an app-level pin if PinRequired is set to True. The possible values are: `numeric`, `alphanumericAndSymbol`. |
| periodBeforePinReset | Duration | TimePeriod before the all-level pin must be reset if PinRequired is set to True. |
| allowedDataStorageLocations | [managedAppDataStorageLocation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdatastoragelocation?view=graph-rest-1.0) collection | Data storage locations where a user may store managed data. |
| contactSyncBlocked | Boolean | Indicates whether contacts can be synced to the user's device. |
| printBlocked | Boolean | Indicates whether printing is allowed from managed apps. |
| fingerprintBlocked | Boolean | Indicates whether use of the fingerprint reader is allowed in place of a pin if PinRequired is set to True. |
| disableAppPinIfDevicePinIsSet | Boolean | Indicates whether use of the app pin is required if the device pin is set. |
| minimumRequiredOsVersion | String | Versions less than the specified version will block the managed app from accessing company data. |
| minimumWarningOsVersion | String | Versions less than the specified version will result in warning message on the managed app from accessing company data. |
| minimumRequiredAppVersion | String | Versions less than the specified version will block the managed app from accessing company data. |
| minimumWarningAppVersion | String | Versions less than the specified version will result in warning message on the managed app. |
| managedBrowser | [managedBrowserType](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedbrowsertype?view=graph-rest-1.0) | Indicates in which managed browser\(s\) that internet links should be opened. When this property is configured, ManagedBrowserToOpenLinksRequired should be true. The possible values are: `notConfigured`, `microsoftEdge`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppProtection",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "version": "String",
  "periodOfflineBeforeAccessCheck": "String (duration)",
  "periodOnlineBeforeAccessCheck": "String (duration)",
  "allowedInboundDataTransferSources": "String",
  "allowedOutboundDataTransferDestinations": "String",
  "organizationalCredentialsRequired": true,
  "allowedOutboundClipboardSharingLevel": "String",
  "dataBackupBlocked": true,
  "deviceComplianceRequired": true,
  "managedBrowserToOpenLinksRequired": true,
  "saveAsBlocked": true,
  "periodOfflineBeforeWipeIsEnforced": "String (duration)",
  "pinRequired": true,
  "maximumPinRetries": 1024,
  "simplePinBlocked": true,
  "minimumPinLength": 1024,
  "pinCharacterSet": "String",
  "periodBeforePinReset": "String (duration)",
  "allowedDataStorageLocations": [
    "String"
  ],
  "contactSyncBlocked": true,
  "printBlocked": true,
  "fingerprintBlocked": true,
  "disableAppPinIfDevicePinIsSet": true,
  "minimumRequiredOsVersion": "String",
  "minimumWarningOsVersion": "String",
  "minimumRequiredAppVersion": "String",
  "minimumWarningAppVersion": "String",
  "managedBrowser": "String"
}
```
