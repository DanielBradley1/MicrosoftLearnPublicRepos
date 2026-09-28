<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsDeliveryOptimizationConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Delivery Optimization configuration

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsDeliveryOptimizationConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsdeliveryoptimizationconfiguration-list?view=graph-rest-beta) | [windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationconfiguration?view=graph-rest-beta) objects. |
| [Get windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsdeliveryoptimizationconfiguration-get?view=graph-rest-beta) | [windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationconfiguration?view=graph-rest-beta) | Read properties and relationships of the [windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationconfiguration?view=graph-rest-beta) object. |
| [Create windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsdeliveryoptimizationconfiguration-create?view=graph-rest-beta) | [windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationconfiguration?view=graph-rest-beta) | Create a new [windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationconfiguration?view=graph-rest-beta) object. |
| [Delete windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsdeliveryoptimizationconfiguration-delete?view=graph-rest-beta) | None | Deletes a [windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationconfiguration?view=graph-rest-beta). |
| [Update windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsdeliveryoptimizationconfiguration-update?view=graph-rest-beta) | [windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationconfiguration?view=graph-rest-beta) | Update the properties of a [windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationconfiguration?view=graph-rest-beta) object. |

## Properties

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
| deliveryOptimizationMode | [windowsDeliveryOptimizationMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationmode?view=graph-rest-beta) | Specifies the download method that delivery optimization can use to manage network bandwidth consumption for large content distribution scenarios. Possible values are: `userDefined`, `httpOnly`, `httpWithPeeringNat`, `httpWithPeeringPrivateGroup`, `httpWithInternetPeering`, `simpleDownload`, `bypassMode`. |
| restrictPeerSelectionBy | [deliveryOptimizationRestrictPeerSelectionByOptions](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deliveryoptimizationrestrictpeerselectionbyoptions?view=graph-rest-beta) | Specifies to restrict peer selection via selected option. |
| Option 1 \(Subnet mask\) only applies to Delivery Optimization modes Download Mode LAN \(1\) and Group \(2\). Possible values are: `notConfigured`, `subnetMask`. |  |  |
| groupIdSource | [deliveryOptimizationGroupIdSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deliveryoptimizationgroupidsource?view=graph-rest-beta) | Specifies to restrict peer selection to a specfic source. |
| The options set in this policy only apply to Delivery Optimization mode Group \(2\) download mode. If Group \(2\) isn't set as Download mode, this policy will be ignored. For option 3 - DHCP Option ID, the client will query DHCP Option ID 234 and use the returned GUID value as the Group ID. |  |  |
| bandwidthMode | [deliveryOptimizationBandwidth](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deliveryoptimizationbandwidth?view=graph-rest-beta) | Specifies foreground and background bandwidth usage using percentages, absolutes, or hours. |
| backgroundDownloadFromHttpDelayInSeconds | Int64 | Specifies number of seconds to delay an HTTP source in a background download that is allowed to use peer-to-peer. Valid values 0 to 4294967295 |
| foregroundDownloadFromHttpDelayInSeconds | Int64 | Specifies number of seconds to delay an HTTP source in a foreground download that is allowed to use peer-to-peer \(0-86400\). Valid values 0 to 86400 |
| Specifying 0 sets Delivery Optimization to manage this setting using the cloud service. Valid values 0 to 86400 |  |  |
| minimumRamAllowedToPeerInGigabytes | Int32 | Specifies the minimum RAM size in GB to use Peer Caching \(1-100000\). Valid values 1 to 100000 |
| minimumDiskSizeAllowedToPeerInGigabytes | Int32 | Specifies the minimum disk size in GB to use Peer Caching \(1-100000\). Valid values 1 to 100000 |
| Recommended values: 64 GB to 256 GB. Valid values 1 to 100000 |  |  |
| minimumFileSizeToCacheInMegabytes | Int32 | Specifies the minimum content file size in MB enabled to use Peer Caching \(1-100000\). Valid values 1 to 100000 |
| Recommended values: 1 MB to 100,000 MB. Valid values 1 to 100000 |  |  |
| minimumBatteryPercentageAllowedToUpload | Int32 | Specifies the minimum battery percentage to allow the device to upload data \(0-100\). Valid values 0 to 100 |
| The default value is 0. The value 0 \(zero\) means "not limited" and the cloud service default value will be used. Valid values 0 to 100 |  |  |
| modifyCacheLocation | String | Specifies the drive that Delivery Optimization should use for its cache. |
| maximumCacheAgeInDays | Int32 | Specifies the maximum time in days that each file is held in the Delivery Optimization cache after downloading successfully \(0-3650\). Valid values 0 to 3650 |
| maximumCacheSize | [deliveryOptimizationMaxCacheSize](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deliveryoptimizationmaxcachesize?view=graph-rest-beta) | Specifies the maximum cache size that Delivery Optimization either as a percentage or in GB. |
| vpnPeerCaching | [enablement](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enablement?view=graph-rest-beta) | Specifies whether the device is allowed to participate in Peer Caching while connected via VPN to the domain network. Possible values are: `notConfigured`, `enabled`, `disabled`. |
| cacheServerHostNames | String collection | Specifies cache servers host names. |
| cacheServerForegroundDownloadFallbackToHttpDelayInSeconds | Int32 | Specifies number of seconds to delay a fall back from cache servers to an HTTP source for a foreground download. Valid values 0 to 2592000.​ |
| cacheServerBackgroundDownloadFallbackToHttpDelayInSeconds | Int32 | Specifies number of seconds to delay a fall back from cache servers to an HTTP source for a background download. Valid values 0 to 2592000. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| groupAssignments | [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) collection | The list of group assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| assignments | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-beta) collection | The list of assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceStatuses | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-beta) collection | Device configuration installation status by device. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| userStatuses | [deviceConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatus?view=graph-rest-beta) collection | Device configuration installation status by user. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceStatusOverview | [deviceConfigurationDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdeviceoverview?view=graph-rest-beta) | Device Configuration devices status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| userStatusOverview | [deviceConfigurationUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuseroverview?view=graph-rest-beta) | Device Configuration users status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceSettingStateSummaries | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-beta) collection | Device Configuration Setting State Device Summary Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsDeliveryOptimizationConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "supportsScopeTags": true,
  "deviceManagementApplicabilityRuleOsEdition": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsEdition",
    "osEditionTypes": [
      "String"
    ],
    "name": "String",
    "ruleType": "String"
  },
  "deviceManagementApplicabilityRuleOsVersion": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsVersion",
    "minOSVersion": "String",
    "maxOSVersion": "String",
    "name": "String",
    "ruleType": "String"
  },
  "deviceManagementApplicabilityRuleDeviceMode": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleDeviceMode",
    "deviceMode": "String",
    "name": "String",
    "ruleType": "String"
  },
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "deliveryOptimizationMode": "String",
  "restrictPeerSelectionBy": "String",
  "groupIdSource": {
    "@odata.type": "microsoft.graph.deliveryOptimizationGroupIdSource"
  },
  "bandwidthMode": {
    "@odata.type": "microsoft.graph.deliveryOptimizationBandwidth"
  },
  "backgroundDownloadFromHttpDelayInSeconds": 1024,
  "foregroundDownloadFromHttpDelayInSeconds": 1024,
  "minimumRamAllowedToPeerInGigabytes": 1024,
  "minimumDiskSizeAllowedToPeerInGigabytes": 1024,
  "minimumFileSizeToCacheInMegabytes": 1024,
  "minimumBatteryPercentageAllowedToUpload": 1024,
  "modifyCacheLocation": "String",
  "maximumCacheAgeInDays": 1024,
  "maximumCacheSize": {
    "@odata.type": "microsoft.graph.deliveryOptimizationMaxCacheSize"
  },
  "vpnPeerCaching": "String",
  "cacheServerHostNames": [
    "String"
  ],
  "cacheServerForegroundDownloadFallbackToHttpDelayInSeconds": 1024,
  "cacheServerBackgroundDownloadFallbackToHttpDelayInSeconds": 1024
}
```
