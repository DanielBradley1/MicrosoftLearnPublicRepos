<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# windows10VpnConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

By providing the configurations in this profile you can instruct the Windows 10 device \(desktop or mobile\) to connect to desired VPN endpoint. By specifying the authentication method and security types expected by VPN endpoint you can make the VPN connection seamless for end user.

Inherits from [windowsVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsvpnconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows10VpnConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10vpnconfiguration-list?view=graph-rest-beta) | [windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconfiguration?view=graph-rest-beta) objects. |
| [Get windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10vpnconfiguration-get?view=graph-rest-beta) | [windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconfiguration?view=graph-rest-beta) | Read properties and relationships of the [windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconfiguration?view=graph-rest-beta) object. |
| [Create windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10vpnconfiguration-create?view=graph-rest-beta) | [windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconfiguration?view=graph-rest-beta) | Create a new [windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconfiguration?view=graph-rest-beta) object. |
| [Delete windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10vpnconfiguration-delete?view=graph-rest-beta) | None | Deletes a [windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconfiguration?view=graph-rest-beta). |
| [Update windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10vpnconfiguration-update?view=graph-rest-beta) | [windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconfiguration?view=graph-rest-beta) | Update the properties of a [windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconfiguration?view=graph-rest-beta) object. |

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
| profileTarget | [windows10VpnProfileTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnprofiletarget?view=graph-rest-beta) | Profile target type. Possible values are: `user`, `device`, `autoPilotDevice`. |
| connectionType | [windows10VpnConnectionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconnectiontype?view=graph-rest-beta) | Connection type. Possible values are: `pulseSecure`, `f5EdgeClient`, `dellSonicWallMobileConnect`, `checkPointCapsuleVpn`, `automatic`, `ikEv2`, `l2tp`, `pptp`, `citrix`, `paloAltoGlobalProtect`, `ciscoAnyConnect`, `unknownFutureValue`, `microsoftTunnel`. |
| enableSplitTunneling | Boolean | Enable split tunneling. |
| enableAlwaysOn | Boolean | Enable Always On mode. |
| enableDeviceTunnel | Boolean | Enable device tunnel. |
| enableDnsRegistration | Boolean | Enable IP address registration with internal DNS. |
| dnsSuffixes | String collection | Specify DNS suffixes to add to the DNS search list to properly route short names. |
| microsoftTunnelSiteId | String | ID of the Microsoft Tunnel site associated with the VPN profile. |
| authenticationMethod | [windows10VpnAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnauthenticationmethod?view=graph-rest-beta) | Authentication method. Possible values are: `certificate`, `usernameAndPassword`, `customEapXml`, `derivedCredential`. |
| rememberUserCredentials | Boolean | Remember user credentials. |
| enableConditionalAccess | Boolean | Enable conditional access. |
| enableSingleSignOnWithAlternateCertificate | Boolean | Enable single sign-on \(SSO\) with alternate certificate. |
| singleSignOnEku | [extendedKeyUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-extendedkeyusage?view=graph-rest-beta) | Single sign-on Extended Key Usage \(EKU\). |
| singleSignOnIssuerHash | String | Single sign-on issuer hash. |
| eapXml | Binary | Extensible Authentication Protocol \(EAP\) XML. \(UTF8 encoded byte array\) |
| proxyServer | [windows10VpnProxyServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnproxyserver?view=graph-rest-beta) | Proxy Server. |
| associatedApps | [windows10AssociatedApps](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10associatedapps?view=graph-rest-beta) collection | Associated Apps. This collection can contain a maximum of 10000 elements. |
| onlyAssociatedAppsCanUseConnection | Boolean | Only associated Apps can use connection \(per-app VPN\). |
| windowsInformationProtectionDomain | String | Windows Information Protection \(WIP\) domain to associate with this connection. |
| trafficRules | [vpnTrafficRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpntrafficrule?view=graph-rest-beta) collection | Traffic rules. This collection can contain a maximum of 1000 elements. |
| routes | [vpnRoute](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnroute?view=graph-rest-beta) collection | Routes \(optional for third-party providers\). This collection can contain a maximum of 1000 elements. |
| dnsRules | [vpnDnsRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpndnsrule?view=graph-rest-beta) collection | DNS rules. This collection can contain a maximum of 1000 elements. |
| trustedNetworkDomains | String collection | Trusted Network Domains |
| cryptographySuite | [cryptographySuite](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-cryptographysuite?view=graph-rest-beta) | Cryptography Suite security settings for IKEv2 VPN in Windows10 and above |

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
| identityCertificate | [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase?view=graph-rest-beta) | Identity certificate for client authentication when authentication method is certificate. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windows10VpnConfiguration",
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
  "profileTarget": "String",
  "connectionType": "String",
  "enableSplitTunneling": true,
  "enableAlwaysOn": true,
  "enableDeviceTunnel": true,
  "enableDnsRegistration": true,
  "dnsSuffixes": [
    "String"
  ],
  "microsoftTunnelSiteId": "String",
  "authenticationMethod": "String",
  "rememberUserCredentials": true,
  "enableConditionalAccess": true,
  "enableSingleSignOnWithAlternateCertificate": true,
  "singleSignOnEku": {
    "@odata.type": "microsoft.graph.extendedKeyUsage",
    "name": "String",
    "objectIdentifier": "String"
  },
  "singleSignOnIssuerHash": "String",
  "eapXml": "binary",
  "proxyServer": {
    "@odata.type": "microsoft.graph.windows10VpnProxyServer",
    "automaticConfigurationScriptUrl": "String",
    "address": "String",
    "port": 1024,
    "bypassProxyServerForLocalAddress": true
  },
  "associatedApps": [
    {
      "@odata.type": "microsoft.graph.windows10AssociatedApps",
      "appType": "String",
      "identifier": "String"
    }
  ],
  "onlyAssociatedAppsCanUseConnection": true,
  "windowsInformationProtectionDomain": "String",
  "trafficRules": [
    {
      "@odata.type": "microsoft.graph.vpnTrafficRule",
      "name": "String",
      "protocols": 1024,
      "localPortRanges": [
        {
          "@odata.type": "microsoft.graph.numberRange",
          "lowerNumber": 1024,
          "upperNumber": 1024
        }
      ],
      "remotePortRanges": [
        {
          "@odata.type": "microsoft.graph.numberRange",
          "lowerNumber": 1024,
          "upperNumber": 1024
        }
      ],
      "localAddressRanges": [
        {
          "@odata.type": "microsoft.graph.iPv4Range",
          "lowerAddress": "String",
          "upperAddress": "String"
        }
      ],
      "remoteAddressRanges": [
        {
          "@odata.type": "microsoft.graph.iPv4Range",
          "lowerAddress": "String",
          "upperAddress": "String"
        }
      ],
      "appId": "String",
      "appType": "String",
      "routingPolicyType": "String",
      "claims": "String",
      "vpnTrafficDirection": "String"
    }
  ],
  "routes": [
    {
      "@odata.type": "microsoft.graph.vpnRoute",
      "destinationPrefix": "String",
      "prefixSize": 1024
    }
  ],
  "dnsRules": [
    {
      "@odata.type": "microsoft.graph.vpnDnsRule",
      "name": "String",
      "servers": [
        "String"
      ],
      "proxyServerUri": "String",
      "autoTrigger": true,
      "persistent": true
    }
  ],
  "trustedNetworkDomains": [
    "String"
  ],
  "cryptographySuite": {
    "@odata.type": "microsoft.graph.cryptographySuite",
    "encryptionMethod": "String",
    "integrityCheckMethod": "String",
    "dhGroup": "String",
    "cipherTransformConstants": "String",
    "authenticationTransformConstants": "String",
    "pfsGroup": "String"
  }
}
```
