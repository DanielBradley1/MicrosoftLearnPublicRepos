<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# iosManagedAppProtection resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Policy used to configure detailed management settings targeted to specific security groups and for a specified set of apps on an iOS device

Inherits from [targetedManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappprotection?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosManagedAppProtections](https://learn.microsoft.com/en-us/graph/api/intune-mam-iosmanagedappprotection-list?view=graph-rest-1.0) | [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) collection | List properties and relationships of the [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) objects. |
| [Get iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-mam-iosmanagedappprotection-get?view=graph-rest-1.0) | [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) | Read properties and relationships of the [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) object. |
| [Create iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-mam-iosmanagedappprotection-create?view=graph-rest-1.0) | [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) | Create a new [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) object. |
| [Delete iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-mam-iosmanagedappprotection-delete?view=graph-rest-1.0) | None | Deletes a [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0). |
| [Update iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-mam-iosmanagedappprotection-update?view=graph-rest-1.0) | [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) | Update the properties of a [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) object. |

## Properties

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
| allowedDataStorageLocations | [managedAppDataStorageLocation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdatastoragelocation?view=graph-rest-1.0) collection | Data storage locations where a user may store managed data. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-1.0) |
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

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [targetedManagedAppPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedapppolicyassignment?view=graph-rest-1.0) collection | Navigation property to list of inclusion and exclusion groups to which the policy is deployed. Inherited from [targetedManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappprotection?view=graph-rest-1.0) |
| apps | [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0) collection | List of apps to which the policy is deployed. |
| deploymentSummary | [managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummary?view=graph-rest-1.0) | Navigation property to deployment summary of the configuration. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosManagedAppProtection",
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
  "managedBrowser": "String",
  "isAssigned": true,
  "appDataEncryptionType": "String",
  "minimumRequiredSdkVersion": "String",
  "deployedAppCount": 1024,
  "faceIdBlocked": true,
  "customBrowserProtocol": "String"
}
```
