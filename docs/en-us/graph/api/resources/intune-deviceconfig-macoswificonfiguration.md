<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# macOSWiFiConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

By providing the configurations in this profile you can instruct the macOS device to connect to desired Wi-Fi endpoint. By specifying the authentication method and security types expected by Wi-Fi endpoint you can make the Wi-Fi connection seamless for end user.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSWiFiConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macoswificonfiguration-list?view=graph-rest-beta) | [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) collection | List properties and relationships of the [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) objects. |
| [Get macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macoswificonfiguration-get?view=graph-rest-beta) | [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) | Read properties and relationships of the [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) object. |
| [Create macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macoswificonfiguration-create?view=graph-rest-beta) | [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) | Create a new [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) object. |
| [Delete macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macoswificonfiguration-delete?view=graph-rest-beta) | None | Deletes a [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta). |
| [Update macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macoswificonfiguration-update?view=graph-rest-beta) | [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) | Update the properties of a [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) object. |

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
| networkName | String | Indicates the Wi-Fi configuration profile name. Used to identify the configuration profile. |
| ssid | String | This is the name of the Wi-Fi network that is broadcast to all devices. |
| connectAutomatically | Boolean | Indicates whether to automatically connect to this network when it is in range of the device. When TRUE will skip the user prompt and automatically connect the device to Wi-Fi network. Default is false. |
| connectWhenNetworkNameIsHidden | Boolean | Indicates whether the device should connect to the network when it is not broadcasting its name \(SSID\). When TRUE, this profile forces the device to connect to a network that doesn't broadcast its SSID to all devices. Default is false. |
| wiFiSecurityType | [wiFiSecurityType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wifisecuritytype?view=graph-rest-beta) | Indicates whether the Wi-Fi endpoint uses an EAP-based security type. Possible values are: open, wpaPersonal, wpaEnterprise, wep, wpa2Personal, and wpa2Enterprise. Possible values are: `open`, `wpaPersonal`, `wpaEnterprise`, `wep`, `wpa2Personal`, `wpa2Enterprise`, `unknownFutureValue`, `wpa3Personal`. |
| proxySettings | [wiFiProxySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wifiproxysetting?view=graph-rest-beta) | Proxy Type for this Wi-Fi connection. Possible values are: `none`, `manual`, `automatic`, `unknownFutureValue`. |
| proxyManualAddress | String | Indicates IP Address or DNS hostname of the proxy server when manual configuration is selected. Used for proxy settings. Example: 10.0.0.2 |
| proxyManualPort | Int32 | Indicates the proxy server TCP port to use when proxySettings is manual. Used for proxy settings. Example: 8080 |
| proxyAutomaticConfigurationUrl | String | Indicates URL of the proxy server automatic configuration \(PAC\) script when proxySettings is automatic. Used to find the location of PAC \(Proxy Auto Configuration\) file. Example: itproxy.contoso.com |
| deploymentChannel | [appleDeploymentChannel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-appledeploymentchannel?view=graph-rest-beta) | Indicates the deployment channel type used to deploy the configuration profile. Once set, cannot be changed. Possible values are deviceChannel, and userChannel. Possible values are: `deviceChannel`, `userChannel`, `unknownFutureValue`. |
| wifiRequirePhysicalMacAddressEnabled | Boolean | Indicates whether devices connecting with this Wi-Fi profile must use their physical MAC address instead of a randomized MAC address. When TRUE, it uses the actual Wi-Fi MAC address. When FALSE, it enables the MAC address randomization. Applies to macOS 15 and later. Default is false. |
| preSharedKey | String | This is the pre-shared key for WPA Personal Wi-Fi network. |

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
  "@odata.type": "#microsoft.graph.macOSWiFiConfiguration",
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
  "networkName": "String",
  "ssid": "String",
  "connectAutomatically": true,
  "connectWhenNetworkNameIsHidden": true,
  "wiFiSecurityType": "String",
  "proxySettings": "String",
  "proxyManualAddress": "String",
  "proxyManualPort": 1024,
  "proxyAutomaticConfigurationUrl": "String",
  "deploymentChannel": "String",
  "wifiRequirePhysicalMacAddressEnabled": true,
  "preSharedKey": "String"
}
```
