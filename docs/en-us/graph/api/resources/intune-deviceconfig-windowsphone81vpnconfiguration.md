<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81vpnconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-12 -->

# windowsPhone81VpnConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

By providing the configurations in this profile you can instruct the Windows Phone 8.1 to connect to desired VPN endpoint. By specifying the authentication method and security types expected by VPN endpoint you can make the VPN connection seamless for end user.

Inherits from [windows81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81vpnconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsPhone81VpnConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81vpnconfiguration-list?view=graph-rest-beta) | [windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81vpnconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81vpnconfiguration?view=graph-rest-beta) objects. |
| [Get windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81vpnconfiguration-get?view=graph-rest-beta) | [windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81vpnconfiguration?view=graph-rest-beta) | Read properties and relationships of the [windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81vpnconfiguration?view=graph-rest-beta) object. |
| [Create windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81vpnconfiguration-create?view=graph-rest-beta) | [windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81vpnconfiguration?view=graph-rest-beta) | Create a new [windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81vpnconfiguration?view=graph-rest-beta) object. |
| [Delete windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81vpnconfiguration-delete?view=graph-rest-beta) | None | Deletes a [windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81vpnconfiguration?view=graph-rest-beta). |
| [Update windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81vpnconfiguration-update?view=graph-rest-beta) | [windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81vpnconfiguration?view=graph-rest-beta) | Update the properties of a [windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81vpnconfiguration?view=graph-rest-beta) object. |

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
| connectionName | String | Connection name displayed to the user. Inherited from [windowsVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsvpnconfiguration?view=graph-rest-beta) |
| servers | [vpnServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnserver?view=graph-rest-beta) collection | List of VPN Servers on the network. Make sure end users can access these network locations. This collection can contain a maximum of 500 elements. Inherited from [windowsVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsvpnconfiguration?view=graph-rest-beta) |
| customXml | Binary | Custom XML commands that configures the VPN connection. \(UTF8 encoded byte array\) Inherited from [windowsVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsvpnconfiguration?view=graph-rest-beta) |
| applyOnlyToWindows81 | Boolean | Value indicating whether this policy only applies to Windows 8.1. This property is read-only. Inherited from [windows81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81vpnconfiguration?view=graph-rest-beta) |
| connectionType | [windowsVpnConnectionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsvpnconnectiontype?view=graph-rest-beta) | Connection type. Inherited from [windows81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81vpnconfiguration?view=graph-rest-beta). Possible values are: `pulseSecure`, `f5EdgeClient`, `dellSonicWallMobileConnect`, `checkPointCapsuleVpn`. |
| loginGroupOrDomain | String | Login group or domain when connection type is set to Dell SonicWALL Mobile Connection. Inherited from [windows81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81vpnconfiguration?view=graph-rest-beta) |
| enableSplitTunneling | Boolean | Enable split tunneling for the VPN. Inherited from [windows81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81vpnconfiguration?view=graph-rest-beta) |
| proxyServer | [windows81VpnProxyServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81vpnproxyserver?view=graph-rest-beta) | Proxy Server. Inherited from [windows81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81vpnconfiguration?view=graph-rest-beta) |
| bypassVpnOnCompanyWifi | Boolean | Bypass VPN on company Wi-Fi. |
| bypassVpnOnHomeWifi | Boolean | Bypass VPN on home Wi-Fi. |
| authenticationMethod | [vpnAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnauthenticationmethod?view=graph-rest-beta) | Authentication method. Possible values are: `certificate`, `usernameAndPassword`, `sharedSecret`, `derivedCredential`, `azureAD`. |
| rememberUserCredentials | Boolean | Remember user credentials. |
| dnsSuffixSearchList | String collection | DNS suffix search list. |

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
| identityCertificate | [windowsPhone81CertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81certificateprofilebase?view=graph-rest-beta) | Identity certificate for client authentication when authentication method is certificate. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsPhone81VpnConfiguration",
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
  "connectionName": "String",
  "servers": [
    {
      "@odata.type": "microsoft.graph.vpnServer",
      "description": "String",
      "address": "String",
      "isDefaultServer": true
    }
  ],
  "customXml": "binary",
  "applyOnlyToWindows81": true,
  "connectionType": "String",
  "loginGroupOrDomain": "String",
  "enableSplitTunneling": true,
  "proxyServer": {
    "@odata.type": "microsoft.graph.windows81VpnProxyServer",
    "automaticConfigurationScriptUrl": "String",
    "address": "String",
    "port": 1024,
    "automaticallyDetectProxySettings": true,
    "bypassProxyServerForLocalAddress": true
  },
  "bypassVpnOnCompanyWifi": true,
  "bypassVpnOnHomeWifi": true,
  "authenticationMethod": "String",
  "rememberUserCredentials": true,
  "dnsSuffixSearchList": [
    "String"
  ]
}
```
