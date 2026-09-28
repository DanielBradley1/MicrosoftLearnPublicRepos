<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosikev2vpnconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-12 -->

# iosikEv2VpnConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

By providing the configurations in this profile you can instruct the iOS device to connect to desired IKEv2 VPN endpoint.

Inherits from [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosikEv2VpnConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosikev2vpnconfiguration-list?view=graph-rest-beta) | [iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosikev2vpnconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosikev2vpnconfiguration?view=graph-rest-beta) objects. |
| [Get iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosikev2vpnconfiguration-get?view=graph-rest-beta) | [iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosikev2vpnconfiguration?view=graph-rest-beta) | Read properties and relationships of the [iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosikev2vpnconfiguration?view=graph-rest-beta) object. |
| [Create iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosikev2vpnconfiguration-create?view=graph-rest-beta) | [iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosikev2vpnconfiguration?view=graph-rest-beta) | Create a new [iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosikev2vpnconfiguration?view=graph-rest-beta) object. |
| [Delete iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosikev2vpnconfiguration-delete?view=graph-rest-beta) | None | Deletes a [iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosikev2vpnconfiguration?view=graph-rest-beta). |
| [Update iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosikev2vpnconfiguration-update?view=graph-rest-beta) | [iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosikev2vpnconfiguration?view=graph-rest-beta) | Update the properties of a [iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosikev2vpnconfiguration?view=graph-rest-beta) object. |

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
| userDomain | String | Zscaler only. Enter a static domain to pre-populate the login field with in the Zscaler app. If this is left empty, the user's Azure Active Directory domain will be used instead. Inherited from [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta) |
| strictEnforcement | Boolean | Zscaler only. Blocks network traffic until the user signs into Zscaler app. "True" means traffic is blocked. Inherited from [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta) |
| cloudName | String | Zscaler only. Zscaler cloud which the user is assigned to. Inherited from [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta) |
| excludeList | String collection | Zscaler only. List of network addresses which are not sent through the Zscaler cloud. Inherited from [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta) |
| targetedMobileApps | [appListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applistitem?view=graph-rest-beta) collection | Targeted mobile apps. This collection can contain a maximum of 500 elements. Inherited from [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta) |
| microsoftTunnelSiteId | String | Microsoft Tunnel site ID. Inherited from [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta) |
| childSecurityAssociationParameters | [iosVpnSecurityAssociationParameters](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnsecurityassociationparameters?view=graph-rest-beta) | Child Security Association Parameters |
| clientAuthenticationType | [vpnClientAuthenticationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnclientauthenticationtype?view=graph-rest-beta) | Type of Client Authentication the VPN client will use. Possible values are: `userAuthentication`, `deviceAuthentication`. |
| deadPeerDetectionRate | [vpnDeadPeerDetectionRate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpndeadpeerdetectionrate?view=graph-rest-beta) | Determine how often to check if a peer connection is still active. . Possible values are: `medium`, `none`, `low`, `high`. |
| disableMobilityAndMultihoming | Boolean | Disable MOBIKE |
| disableRedirect | Boolean | Disable Redirect |
| enableCertificateRevocationCheck | Boolean | Enables a best-effort revocation check; server response timeouts will not cause it to fail |
| enableEAP | Boolean | Enables EAP only authentication |
| enablePerfectForwardSecrecy | Boolean | Enable Perfect Forward Secrecy \(PFS\). |
| enableUseInternalSubnetAttributes | Boolean | Enable Use Internal Subnet Attributes. |
| localIdentifier | [vpnLocalIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnlocalidentifier?view=graph-rest-beta) | Method of identifying the client that is trying to connect via VPN. . Possible values are: `deviceFQDN`, `empty`, `clientCertificateSubjectName`. |
| remoteIdentifier | String | Address of the IKEv2 server. Must be a FQDN, UserFQDN, network address, or ASN1DN |
| securityAssociationParameters | [iosVpnSecurityAssociationParameters](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnsecurityassociationparameters?view=graph-rest-beta) | Security Association Parameters |
| serverCertificateCommonName | String | Common name of the IKEv2 Server Certificate used in Server Authentication |
| serverCertificateIssuerCommonName | String | Issuer Common name of the IKEv2 Server Certificate issuer used in Authentication |
| serverCertificateType | [vpnServerCertificateType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnservercertificatetype?view=graph-rest-beta) | The type of certificate the VPN server will present to the VPN client for authentication. Possible values are: `rsa`, `ecdsa256`, `ecdsa384`, `ecdsa521`. |
| sharedSecret | String | Used when Shared Secret Authentication is selected |
| tlsMaximumVersion | String | The maximum TLS version to be used with EAP-TLS authentication |
| tlsMinimumVersion | String | The minimum TLS version to be used with EAP-TLS authentication |
| allowDefaultSecurityAssociationParameters | Boolean | Allows the use of security association parameters by setting all parameters to the device's default unless explicitly specified. |
| allowDefaultChildSecurityAssociationParameters | Boolean | Allows the use of child security association parameters by setting all parameters to the device's default unless explicitly specified. |
| alwaysOnConfiguration | [appleVpnAlwaysOnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnalwaysonconfiguration?view=graph-rest-beta) | AlwaysOn Configuration |
| enableAlwaysOnConfiguration | Boolean | Determines if Always on VPN is enabled |
| mtuSizeInBytes | Int32 | Maximum transmission unit. Valid values 1280 to 1400 |

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
| identityCertificate | [iosCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofilebase?view=graph-rest-beta) | Identity certificate for client authentication when authentication method is certificate. Inherited from [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta) |
| derivedCredentialSettings | [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) | Tenant level settings for the Derived Credentials to be used for authentication. Inherited from [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosikEv2VpnConfiguration",
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
  "connectionType": "String",
  "loginGroupOrDomain": "String",
  "role": "String",
  "realm": "String",
  "server": {
    "@odata.type": "microsoft.graph.vpnServer",
    "description": "String",
    "address": "String",
    "isDefaultServer": true
  },
  "identifier": "String",
  "customData": [
    {
      "@odata.type": "microsoft.graph.keyValue",
      "key": "String",
      "value": "String"
    }
  ],
  "customKeyValueData": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "String",
      "value": "String"
    }
  ],
  "enableSplitTunneling": true,
  "authenticationMethod": "String",
  "enablePerApp": true,
  "safariDomains": [
    "String"
  ],
  "onDemandRules": [
    {
      "@odata.type": "microsoft.graph.vpnOnDemandRule",
      "ssids": [
        "String"
      ],
      "dnsSearchDomains": [
        "String"
      ],
      "probeUrl": "String",
      "action": "String",
      "domainAction": "String",
      "domains": [
        "String"
      ],
      "probeRequiredUrl": "String",
      "interfaceTypeMatch": "String",
      "dnsServerAddressMatch": [
        "String"
      ]
    }
  ],
  "providerType": "String",
  "associatedDomains": [
    "String"
  ],
  "excludedDomains": [
    "String"
  ],
  "disableOnDemandUserOverride": true,
  "disconnectOnIdle": true,
  "disconnectOnIdleTimerInSeconds": 1024,
  "proxyServer": {
    "@odata.type": "microsoft.graph.vpnProxyServer",
    "automaticConfigurationScriptUrl": "String",
    "address": "String",
    "port": 1024
  },
  "optInToDeviceIdSharing": true,
  "userDomain": "String",
  "strictEnforcement": true,
  "cloudName": "String",
  "excludeList": [
    "String"
  ],
  "targetedMobileApps": [
    {
      "@odata.type": "microsoft.graph.appListItem",
      "name": "String",
      "publisher": "String",
      "appStoreUrl": "String",
      "appId": "String"
    }
  ],
  "microsoftTunnelSiteId": "String",
  "childSecurityAssociationParameters": {
    "@odata.type": "microsoft.graph.iosVpnSecurityAssociationParameters",
    "securityEncryptionAlgorithm": "String",
    "securityIntegrityAlgorithm": "String",
    "securityDiffieHellmanGroup": 1024,
    "lifetimeInMinutes": 1024
  },
  "clientAuthenticationType": "String",
  "deadPeerDetectionRate": "String",
  "disableMobilityAndMultihoming": true,
  "disableRedirect": true,
  "enableCertificateRevocationCheck": true,
  "enableEAP": true,
  "enablePerfectForwardSecrecy": true,
  "enableUseInternalSubnetAttributes": true,
  "localIdentifier": "String",
  "remoteIdentifier": "String",
  "securityAssociationParameters": {
    "@odata.type": "microsoft.graph.iosVpnSecurityAssociationParameters",
    "securityEncryptionAlgorithm": "String",
    "securityIntegrityAlgorithm": "String",
    "securityDiffieHellmanGroup": 1024,
    "lifetimeInMinutes": 1024
  },
  "serverCertificateCommonName": "String",
  "serverCertificateIssuerCommonName": "String",
  "serverCertificateType": "String",
  "sharedSecret": "String",
  "tlsMaximumVersion": "String",
  "tlsMinimumVersion": "String",
  "allowDefaultSecurityAssociationParameters": true,
  "allowDefaultChildSecurityAssociationParameters": true,
  "alwaysOnConfiguration": {
    "@odata.type": "microsoft.graph.appleVpnAlwaysOnConfiguration",
    "tunnelConfiguration": "String",
    "userToggleEnabled": true,
    "voicemailExceptionAction": "String",
    "airPrintExceptionAction": "String",
    "cellularExceptionAction": "String",
    "allowAllCaptiveNetworkPlugins": true,
    "allowedCaptiveNetworkPlugins": {
      "@odata.type": "microsoft.graph.specifiedCaptiveNetworkPlugins",
      "allowedBundleIdentifiers": [
        "String"
      ]
    },
    "allowCaptiveWebSheet": true,
    "natKeepAliveIntervalInSeconds": 1024,
    "natKeepAliveOffloadEnable": true
  },
  "enableAlwaysOnConfiguration": true,
  "mtuSizeInBytes": 1024
}
```
