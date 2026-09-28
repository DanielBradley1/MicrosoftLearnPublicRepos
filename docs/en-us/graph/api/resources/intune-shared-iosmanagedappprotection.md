<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# iosManagedAppProtection resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Policy used to configure detailed management settings targeted to specific security groups and for a specified set of apps on an iOS device

Inherits from [targetedManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappprotection?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosManagedAppProtections](https://learn.microsoft.com/en-us/graph/api/intune-shared-iosmanagedappprotection-list?view=graph-rest-beta) | [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta) collection | List properties and relationships of the [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta) objects. |
| [Get iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-shared-iosmanagedappprotection-get?view=graph-rest-beta) | [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta) | Read properties and relationships of the [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta) object. |
| [Create iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-shared-iosmanagedappprotection-create?view=graph-rest-beta) | [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta) | Create a new [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta) object. |
| [Delete iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-shared-iosmanagedappprotection-delete?view=graph-rest-beta) | None | Deletes a [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta). |
| [Update iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-shared-iosmanagedappprotection-update?view=graph-rest-beta) | [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta) | Update the properties of a [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta) object. |
| **Policy Set** |  |  |
| [hasPayloadLinks action](https://learn.microsoft.com/en-us/graph/api/intune-shared-iosmanagedappprotection-haspayloadlinks?view=graph-rest-beta) | [hasPayloadLinkResultItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-haspayloadlinkresultitem?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| displayName | String | Policy display name. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| description | String | The policy's description. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The date and time the policy was created. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | Last time the policy was modified. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| version | String | Version of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| periodOfflineBeforeAccessCheck | Duration | The period after which access is checked when the device is not connected to the internet. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| periodOnlineBeforeAccessCheck | Duration | The period after which access is checked when the device is connected to the internet. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| allowedInboundDataTransferSources | [managedAppDataTransferLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdatatransferlevel?view=graph-rest-beta) | Sources from which data is allowed to be transferred. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta). The possible values are: `allApps`, `managedApps`, `none`. |
| allowedOutboundDataTransferDestinations | [managedAppDataTransferLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdatatransferlevel?view=graph-rest-beta) | Destinations to which data is allowed to be transferred. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta). The possible values are: `allApps`, `managedApps`, `none`. |
| organizationalCredentialsRequired | Boolean | Indicates whether organizational credentials are required for app use. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| allowedOutboundClipboardSharingLevel | [managedAppClipboardSharingLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappclipboardsharinglevel?view=graph-rest-beta) | The level to which the clipboard may be shared between apps on the managed device. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta). The possible values are: `allApps`, `managedAppsWithPasteIn`, `managedApps`, `blocked`. |
| dataBackupBlocked | Boolean | Indicates whether the backup of a managed app's data is blocked. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| deviceComplianceRequired | Boolean | Indicates whether device compliance is required. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| managedBrowserToOpenLinksRequired | Boolean | Indicates whether internet links should be opened in the managed browser app. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| saveAsBlocked | Boolean | Indicates whether users may use the "Save As" menu item to save a copy of protected files. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| periodOfflineBeforeWipeIsEnforced | Duration | The amount of time an app is allowed to remain disconnected from the internet before all managed data it is wiped. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| pinRequired | Boolean | Indicates whether an app-level pin is required. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| maximumPinRetries | Int32 | Maximum number of incorrect pin retry attempts before the managed app is either blocked or wiped. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| simplePinBlocked | Boolean | Indicates whether simplePin is blocked. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| minimumPinLength | Int32 | Minimum pin length required for an app-level pin if PinRequired is set to True Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| pinCharacterSet | [managedAppPinCharacterSet](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppincharacterset?view=graph-rest-beta) | Character set which may be used for an app-level pin if PinRequired is set to True. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta). The possible values are: `numeric`, `alphanumericAndSymbol`. |
| periodBeforePinReset | Duration | TimePeriod before the all-level pin must be reset if PinRequired is set to True. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| allowedDataStorageLocations | [managedAppDataStorageLocation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdatastoragelocation?view=graph-rest-beta) collection | Data storage locations where a user may store managed data. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| contactSyncBlocked | Boolean | Indicates whether contacts can be synced to the user's device. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| printBlocked | Boolean | Indicates whether printing is allowed from managed apps. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| fingerprintBlocked | Boolean | Indicates whether use of the fingerprint reader is allowed in place of a pin if PinRequired is set to True. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| disableAppPinIfDevicePinIsSet | Boolean | Indicates whether use of the app pin is required if the device pin is set. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| minimumRequiredOsVersion | String | Versions less than the specified version will block the managed app from accessing company data. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| minimumWarningOsVersion | String | Versions less than the specified version will result in warning message on the managed app from accessing company data. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| minimumRequiredAppVersion | String | Versions less than the specified version will block the managed app from accessing company data. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| minimumWarningAppVersion | String | Versions less than the specified version will result in warning message on the managed app. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| minimumWipeOsVersion | String | Versions less than or equal to the specified version will wipe the managed app and the associated company data. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| minimumWipeAppVersion | String | Versions less than or equal to the specified version will wipe the managed app and the associated company data. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| appActionIfDeviceComplianceRequired | [managedAppRemediationAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappremediationaction?view=graph-rest-beta) | Defines a managed app behavior, either block or wipe, when the device is either rooted or jailbroken, if DeviceComplianceRequired is set to true. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta). The possible values are: `block`, `wipe`, `warn`. |
| appActionIfMaximumPinRetriesExceeded | [managedAppRemediationAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappremediationaction?view=graph-rest-beta) | Defines a managed app behavior, either block or wipe, based on maximum number of incorrect pin retry attempts. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta). The possible values are: `block`, `wipe`, `warn`. |
| pinRequiredInsteadOfBiometricTimeout | Duration | Timeout in minutes for an app pin instead of non biometrics passcode Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| allowedOutboundClipboardSharingExceptionLength | Int32 | Specify the number of characters that may be cut or copied from Org data and accounts to any application. This setting overrides the AllowedOutboundClipboardSharingLevel restriction. Default value of '0' means no exception is allowed. Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta) |
| notificationRestriction | [managedAppNotificationRestriction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappnotificationrestriction?view=graph-rest-beta) | Specify app notification restriction Inherited from [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection?view=graph-rest-beta). The possible values are: `allow`, `blockOrganizationalData`, `block`. |
| isAssigned | Boolean | Indicates if the policy is deployed to any inclusion groups or not. Inherited from [targetedManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappprotection?view=graph-rest-beta) |
| targetedAppManagementLevels | [appManagementLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-appmanagementlevel?view=graph-rest-beta) | The intended app management levels for this policy Inherited from [targetedManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappprotection?view=graph-rest-beta). The possible values are: `unspecified`, `unmanaged`, `mdm`, `androidEnterprise`. |
| appDataEncryptionType | [managedAppDataEncryptionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdataencryptiontype?view=graph-rest-beta) | Type of encryption which should be used for data in a managed app. The possible values are: `useDeviceSettings`, `afterDeviceRestart`, `whenDeviceLockedExceptOpenFiles`, `whenDeviceLocked`. |
| minimumRequiredSdkVersion | String | Versions less than the specified version will block the managed app from accessing company data. |
| deployedAppCount | Int32 | Count of apps to which the current policy is deployed. |
| faceIdBlocked | Boolean | Indicates whether use of the FaceID is allowed in place of a pin if PinRequired is set to True. |
| exemptedAppProtocols | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keyvaluepair?view=graph-rest-beta) collection | Apps in this list will be exempt from the policy and will be able to receive data from managed apps. |
| minimumWipeSdkVersion | String | Versions less than the specified version will block the managed app from accessing company data. |
| allowedIosDeviceModels | String | Semicolon seperated list of device models allowed, as a string, for the managed app to work. |
| appActionIfIosDeviceModelNotAllowed | [managedAppRemediationAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappremediationaction?view=graph-rest-beta) | Defines a managed app behavior, either block or wipe, if the specified device model is not allowed. The possible values are: `block`, `wipe`, `warn`. |
| filterOpenInToOnlyManagedApps | Boolean | Defines if open-in operation is supported from the managed app to the filesharing locations selected. This setting only applies when AllowedOutboundDataTransferDestinations is set to ManagedApps and DisableProtectionOfManagedOutboundOpenInData is set to False. |
| disableProtectionOfManagedOutboundOpenInData | Boolean | Disable protection of data transferred to other apps through IOS OpenIn option. This setting is only allowed to be True when AllowedOutboundDataTransferDestinations is set to ManagedApps. |
| protectInboundDataFromUnknownSources | Boolean | Protect incoming data from unknown source. This setting is only allowed to be True when AllowedInboundDataTransferSources is set to AllApps. |
| customBrowserProtocol | String | A custom browser protocol to open weblink on iOS. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| **Mobile app management \(MAM\)** |  |  |
| assignments | [targetedManagedAppPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedapppolicyassignment?view=graph-rest-beta) collection | Navigation property to list of inclusion and exclusion groups to which the policy is deployed. Inherited from [targetedManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappprotection?view=graph-rest-beta) |
| apps | [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-beta) collection | List of apps to which the policy is deployed. |
| deploymentSummary | [managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummary?view=graph-rest-beta) | Navigation property to deployment summary of the configuration. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosManagedAppProtection",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
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
  "minimumWipeOsVersion": "String",
  "minimumWipeAppVersion": "String",
  "appActionIfDeviceComplianceRequired": "String",
  "appActionIfMaximumPinRetriesExceeded": "String",
  "pinRequiredInsteadOfBiometricTimeout": "String (duration)",
  "allowedOutboundClipboardSharingExceptionLength": 1024,
  "notificationRestriction": "String",
  "isAssigned": true,
  "targetedAppManagementLevels": "String",
  "appDataEncryptionType": "String",
  "minimumRequiredSdkVersion": "String",
  "deployedAppCount": 1024,
  "faceIdBlocked": true,
  "exemptedAppProtocols": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "String",
      "value": "String"
    }
  ],
  "minimumWipeSdkVersion": "String",
  "allowedIosDeviceModels": "String",
  "appActionIfIosDeviceModelNotAllowed": "String",
  "filterOpenInToOnlyManagedApps": true,
  "disableProtectionOfManagedOutboundOpenInData": true,
  "protectInboundDataFromUnknownSources": true,
  "customBrowserProtocol": "String"
}
```
