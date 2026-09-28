<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappprotection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsManagedAppProtection resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Policy used to configure detailed management settings targeted to specific security groups and for a specified set of apps on a Windows device

Inherits from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsManagedAppProtections](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappprotection-list?view=graph-rest-beta) | [windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappprotection?view=graph-rest-beta) collection | List properties and relationships of the [windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappprotection?view=graph-rest-beta) objects. |
| [Get windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappprotection-get?view=graph-rest-beta) | [windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappprotection?view=graph-rest-beta) | Read properties and relationships of the [windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappprotection?view=graph-rest-beta) object. |
| [Create windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappprotection-create?view=graph-rest-beta) | [windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappprotection?view=graph-rest-beta) | Create a new [windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappprotection?view=graph-rest-beta) object. |
| [Delete windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappprotection-delete?view=graph-rest-beta) | None | Deletes a [windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappprotection?view=graph-rest-beta). |
| [Update windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappprotection-update?view=graph-rest-beta) | [windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappprotection?view=graph-rest-beta) | Update the properties of a [windowsManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappprotection?view=graph-rest-beta) object. |
| [targetApps action](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappprotection-targetapps?view=graph-rest-beta) | None |  |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappprotection-assign?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Policy display name. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| description | String | The policy's description. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The date and time the policy was created. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | Last time the policy was modified. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| version | String | Version of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| isAssigned | Boolean | When TRUE, indicates that the policy is deployed to some inclusion groups. When FALSE, indicates that the policy is not deployed to any inclusion groups. Default value is FALSE. |
| deployedAppCount | Int32 | Indicates the total number of applications for which the current policy is deployed. |
| printBlocked | Boolean | When TRUE, indicates that printing is blocked from managed apps. When FALSE, indicates that printing is allowed from managed apps. Default value is FALSE. |
| allowedInboundDataTransferSources | [windowsManagedAppDataTransferLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappdatatransferlevel?view=graph-rest-beta) | Indicates the sources from which data is allowed to be transferred. Some possible values are allApps or none. Possible values are: `allApps`, `none`. |
| allowedOutboundClipboardSharingLevel | [windowsManagedAppClipboardSharingLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappclipboardsharinglevel?view=graph-rest-beta) | Indicates the level to which the clipboard may be shared across org & non-org resources. Some possible values are anyDestinationAnySource or none. Possible values are: `anyDestinationAnySource`, `none`, `orgDestinationAnySource`, `orgDestinationOrgSource`, `unknownFutureValue`. |
| allowedOutboundDataTransferDestinations | [windowsManagedAppDataTransferLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappdatatransferlevel?view=graph-rest-beta) | Indicates the destinations to which data is allowed to be transferred. Some possible values are allApps or none. Possible values are: `allApps`, `none`. |
| appActionIfUnableToAuthenticateUser | [managedAppRemediationAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappremediationaction?view=graph-rest-beta) | If set, it will specify what action to take in the case where the user is unable to checkin because their authentication token is invalid. This happens when the user is deleted or disabled in AAD. Some possible values are block or wipe. If this property is not set, no action will be taken. Possible values are: `block`, `wipe`, `warn`, `blockWhenSettingIsSupported`. |
| maximumAllowedDeviceThreatLevel | [managedAppDeviceThreatLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdevicethreatlevel?view=graph-rest-beta) | Maximum allowed device threat level, as reported by the Mobile Threat Defense app. Possible values are: `notConfigured`, `secured`, `low`, `medium`, `high`. |
| mobileThreatDefenseRemediationAction | [managedAppRemediationAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappremediationaction?view=graph-rest-beta) | Determines what action to take if the mobile threat defense threat threshold isn't met. Some possible values are block or wipe. Warn isn't a supported value for this property. Possible values are: `block`, `wipe`, `warn`, `blockWhenSettingIsSupported`. |
| minimumRequiredSdkVersion | String | Versions less than the specified version will block the managed app from accessing company data. For example: '8.1.0' or '13.1.1'. |
| minimumWipeSdkVersion | String | Versions less than the specified version will wipe the managed app and the associated company data. For example: '8.1.0' or '13.1.1'. |
| minimumRequiredOsVersion | String | Versions less than the specified version will block the managed app from accessing company data. For example: '8.1.0' or '13.1.1'. |
| minimumWarningOsVersion | String | Versions less than the specified version will result in warning message on the managed app from accessing company data. For example: '8.1.0' or '13.1.1'. |
| minimumWipeOsVersion | String | Versions less than the specified version will wipe the managed app and the associated company data. For example: '8.1.0' or '13.1.1'. |
| minimumRequiredAppVersion | String | Versions less than the specified version will block the managed app from accessing company data. For example: '8.1.0' or '13.1.1'. |
| minimumWarningAppVersion | String | Versions less than the specified version will result in warning message on the managed app from accessing company data. For example: '8.1.0' or '13.1.1'. |
| minimumWipeAppVersion | String | Versions less than the specified version will wipe the managed app and the associated company data. For example: '8.1.0' or '13.1.1'. |
| maximumRequiredOsVersion | String | Versions bigger than the specified version will block the managed app from accessing company data. For example: '8.1.0' or '13.1.1'. |
| maximumWarningOsVersion | String | Versions bigger than the specified version will result in warning message on the managed app from accessing company data. For example: '8.1.0' or '13.1.1'. |
| maximumWipeOsVersion | String | Versions bigger than the specified version will wipe the managed app and the associated company data. For example: '8.1.0' or '13.1.1'. |
| periodOfflineBeforeWipeIsEnforced | Duration | The amount of time an app is allowed to remain disconnected from the internet before all managed data it is wiped. For example, P5D indicates that the interval is 5 days in duration. A timespan value of PT0S indicates that managed data will never be wiped when the device is not connected to the internet. |
| periodOfflineBeforeAccessCheck | Duration | The period after which access is checked when the device is not connected to the internet. For example, PT5M indicates that the interval is 5 minutes in duration. A timespan value of PT0S indicates that access will be blocked immediately when the device is not connected to the internet. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [targetedManagedAppPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedapppolicyassignment?view=graph-rest-beta) collection | Navigation property to list of inclusion and exclusion groups to which the policy is deployed. |
| apps | [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-beta) collection | List of apps to which the policy is deployed. |
| deploymentSummary | [managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummary?view=graph-rest-beta) | Navigation property to deployment summary of the configuration. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsManagedAppProtection",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "id": "String (identifier)",
  "version": "String",
  "isAssigned": true,
  "deployedAppCount": 1024,
  "printBlocked": true,
  "allowedInboundDataTransferSources": "String",
  "allowedOutboundClipboardSharingLevel": "String",
  "allowedOutboundDataTransferDestinations": "String",
  "appActionIfUnableToAuthenticateUser": "String",
  "maximumAllowedDeviceThreatLevel": "String",
  "mobileThreatDefenseRemediationAction": "String",
  "minimumRequiredSdkVersion": "String",
  "minimumWipeSdkVersion": "String",
  "minimumRequiredOsVersion": "String",
  "minimumWarningOsVersion": "String",
  "minimumWipeOsVersion": "String",
  "minimumRequiredAppVersion": "String",
  "minimumWarningAppVersion": "String",
  "minimumWipeAppVersion": "String",
  "maximumRequiredOsVersion": "String",
  "maximumWarningOsVersion": "String",
  "maximumWipeOsVersion": "String",
  "periodOfflineBeforeWipeIsEnforced": "String (duration)",
  "periodOfflineBeforeAccessCheck": "String (duration)"
}
```
