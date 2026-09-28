<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosvpnconfiguration-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# Update iosVpnConfiguration

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta) object.

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
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/groupAssignments/{deviceConfigurationGroupAssignmentId}/deviceConfiguration
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.windowsDomainJoinConfiguration/networkAccessConfigurations/{deviceConfigurationId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta).

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
| connectionName | String | Connection name displayed to the user. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| connectionType | [appleVpnConnectionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconnectiontype?view=graph-rest-beta) | Connection type. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta). Possible values are: `ciscoAnyConnect`, `pulseSecure`, `f5EdgeClient`, `dellSonicWallMobileConnect`, `checkPointCapsuleVpn`, `customVpn`, `ciscoIPSec`, `citrix`, `ciscoAnyConnectV2`, `paloAltoGlobalProtect`, `zscalerPrivateAccess`, `f5Access2018`, `citrixSso`, `paloAltoGlobalProtectV2`, `ikEv2`, `alwaysOn`, `microsoftTunnel`, `netMotionMobility`, `microsoftProtect`. |
| loginGroupOrDomain | String | Login group or domain when connection type is set to Dell SonicWALL Mobile Connection. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| role | String | Role when connection type is set to Pulse Secure. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| realm | String | Realm when connection type is set to Pulse Secure. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| server | [vpnServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnserver?view=graph-rest-beta) | VPN Server on the network. Make sure end users can access this network location. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| identifier | String | Identifier provided by VPN vendor when connection type is set to Custom VPN. For example: Cisco AnyConnect uses an identifier of the form com.cisco.anyconnect.applevpn.plugin Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| customData | [keyValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-keyvalue?view=graph-rest-beta) collection | Custom data when connection type is set to Custom VPN. Use this field to enable functionality not supported by Intune, but available in your VPN solution. Contact your VPN vendor to learn how to add these key/value pairs. This collection can contain a maximum of 25 elements. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| customKeyValueData | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-keyvaluepair?view=graph-rest-beta) collection | Custom data when connection type is set to Custom VPN. Use this field to enable functionality not supported by Intune, but available in your VPN solution. Contact your VPN vendor to learn how to add these key/value pairs. This collection can contain a maximum of 25 elements. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| enableSplitTunneling | Boolean | Send all network traffic through VPN. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| authenticationMethod | [vpnAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnauthenticationmethod?view=graph-rest-beta) | Authentication method for this VPN connection. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta). Possible values are: `certificate`, `usernameAndPassword`, `sharedSecret`, `derivedCredential`, `azureAD`. |
| enablePerApp | Boolean | Setting this to true creates Per-App VPN payload which can later be associated with Apps that can trigger this VPN conneciton on the end user's iOS device. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| safariDomains | String collection | Safari domains when this VPN per App setting is enabled. In addition to the apps associated with this VPN, Safari domains specified here will also be able to trigger this VPN connection. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| onDemandRules | [vpnOnDemandRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnondemandrule?view=graph-rest-beta) collection | On-Demand Rules. This collection can contain a maximum of 500 elements. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| providerType | [vpnProviderType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnprovidertype?view=graph-rest-beta) | Provider type for per-app VPN. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta). Possible values are: `notConfigured`, `appProxy`, `packetTunnel`. |
| associatedDomains | String collection | Associated Domains Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| excludedDomains | String collection | Domains that are accessed through the public internet instead of through VPN, even when per-app VPN is activated Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| disableOnDemandUserOverride | Boolean | Toggle to prevent user from disabling automatic VPN in the Settings app Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| disconnectOnIdle | Boolean | Whether to disconnect after on-demand connection idles Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| disconnectOnIdleTimerInSeconds | Int32 | The length of time in seconds to wait before disconnecting an on-demand connection. Valid values 0 to 65535 Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| proxyServer | [vpnProxyServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnproxyserver?view=graph-rest-beta) | Proxy Server. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| optInToDeviceIdSharing | Boolean | Opt-In to sharing the device's Id to third-party vpn clients for use during network access control validation. Inherited from [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration?view=graph-rest-beta) |
| userDomain | String | Zscaler only. Enter a static domain to pre-populate the login field with in the Zscaler app. If this is left empty, the user's Azure Active Directory domain will be used instead. |
| strictEnforcement | Boolean | Zscaler only. Blocks network traffic until the user signs into Zscaler app. "True" means traffic is blocked. |
| cloudName | String | Zscaler only. Zscaler cloud which the user is assigned to. |
| excludeList | String collection | Zscaler only. List of network addresses which are not sent through the Zscaler cloud. |
| targetedMobileApps | [appListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applistitem?view=graph-rest-beta) collection | Targeted mobile apps. This collection can contain a maximum of 500 elements. |
| microsoftTunnelSiteId | String | Microsoft Tunnel site ID. |

## Response

If successful, this method returns a `200 OK` response code and an updated [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations/{deviceConfigurationId}
Content-type: application/json
Content-length: 3495

{
  "@odata.type": "#microsoft.graph.iosVpnConfiguration",
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
  "connectionName": "Connection Name value",
  "connectionType": "pulseSecure",
  "loginGroupOrDomain": "Login Group Or Domain value",
  "role": "Role value",
  "realm": "Realm value",
  "server": {
    "@odata.type": "microsoft.graph.vpnServer",
    "description": "Description value",
    "address": "Address value",
    "isDefaultServer": true
  },
  "identifier": "Identifier value",
  "customData": [
    {
      "@odata.type": "microsoft.graph.keyValue",
      "key": "Key value",
      "value": "Value value"
    }
  ],
  "customKeyValueData": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "Name value",
      "value": "Value value"
    }
  ],
  "enableSplitTunneling": true,
  "authenticationMethod": "usernameAndPassword",
  "enablePerApp": true,
  "safariDomains": [
    "Safari Domains value"
  ],
  "onDemandRules": [
    {
      "@odata.type": "microsoft.graph.vpnOnDemandRule",
      "ssids": [
        "Ssids value"
      ],
      "dnsSearchDomains": [
        "Dns Search Domains value"
      ],
      "probeUrl": "https://example.com/probeUrl/",
      "action": "evaluateConnection",
      "domainAction": "neverConnect",
      "domains": [
        "Domains value"
      ],
      "probeRequiredUrl": "https://example.com/probeRequiredUrl/",
      "interfaceTypeMatch": "ethernet",
      "dnsServerAddressMatch": [
        "Dns Server Address Match value"
      ]
    }
  ],
  "providerType": "appProxy",
  "associatedDomains": [
    "Associated Domains value"
  ],
  "excludedDomains": [
    "Excluded Domains value"
  ],
  "disableOnDemandUserOverride": true,
  "disconnectOnIdle": true,
  "disconnectOnIdleTimerInSeconds": 14,
  "proxyServer": {
    "@odata.type": "microsoft.graph.vpnProxyServer",
    "automaticConfigurationScriptUrl": "https://example.com/automaticConfigurationScriptUrl/",
    "address": "Address value",
    "port": 4
  },
  "optInToDeviceIdSharing": true,
  "userDomain": "User Domain value",
  "strictEnforcement": true,
  "cloudName": "Cloud Name value",
  "excludeList": [
    "Exclude List value"
  ],
  "targetedMobileApps": [
    {
      "@odata.type": "microsoft.graph.appListItem",
      "name": "Name value",
      "publisher": "Publisher value",
      "appStoreUrl": "https://example.com/appStoreUrl/",
      "appId": "App Id value"
    }
  ],
  "microsoftTunnelSiteId": "Microsoft Tunnel Site Id value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 3667

{
  "@odata.type": "#microsoft.graph.iosVpnConfiguration",
  "id": "bd12424c-424c-bd12-4c42-12bd4c4212bd",
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
  "connectionName": "Connection Name value",
  "connectionType": "pulseSecure",
  "loginGroupOrDomain": "Login Group Or Domain value",
  "role": "Role value",
  "realm": "Realm value",
  "server": {
    "@odata.type": "microsoft.graph.vpnServer",
    "description": "Description value",
    "address": "Address value",
    "isDefaultServer": true
  },
  "identifier": "Identifier value",
  "customData": [
    {
      "@odata.type": "microsoft.graph.keyValue",
      "key": "Key value",
      "value": "Value value"
    }
  ],
  "customKeyValueData": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "Name value",
      "value": "Value value"
    }
  ],
  "enableSplitTunneling": true,
  "authenticationMethod": "usernameAndPassword",
  "enablePerApp": true,
  "safariDomains": [
    "Safari Domains value"
  ],
  "onDemandRules": [
    {
      "@odata.type": "microsoft.graph.vpnOnDemandRule",
      "ssids": [
        "Ssids value"
      ],
      "dnsSearchDomains": [
        "Dns Search Domains value"
      ],
      "probeUrl": "https://example.com/probeUrl/",
      "action": "evaluateConnection",
      "domainAction": "neverConnect",
      "domains": [
        "Domains value"
      ],
      "probeRequiredUrl": "https://example.com/probeRequiredUrl/",
      "interfaceTypeMatch": "ethernet",
      "dnsServerAddressMatch": [
        "Dns Server Address Match value"
      ]
    }
  ],
  "providerType": "appProxy",
  "associatedDomains": [
    "Associated Domains value"
  ],
  "excludedDomains": [
    "Excluded Domains value"
  ],
  "disableOnDemandUserOverride": true,
  "disconnectOnIdle": true,
  "disconnectOnIdleTimerInSeconds": 14,
  "proxyServer": {
    "@odata.type": "microsoft.graph.vpnProxyServer",
    "automaticConfigurationScriptUrl": "https://example.com/automaticConfigurationScriptUrl/",
    "address": "Address value",
    "port": 4
  },
  "optInToDeviceIdSharing": true,
  "userDomain": "User Domain value",
  "strictEnforcement": true,
  "cloudName": "Cloud Name value",
  "excludeList": [
    "Exclude List value"
  ],
  "targetedMobileApps": [
    {
      "@odata.type": "microsoft.graph.appListItem",
      "name": "Name value",
      "publisher": "Publisher value",
      "appStoreUrl": "https://example.com/appStoreUrl/",
      "appId": "App Id value"
    }
  ],
  "microsoftTunnelSiteId": "Microsoft Tunnel Site Id value"
}
```
