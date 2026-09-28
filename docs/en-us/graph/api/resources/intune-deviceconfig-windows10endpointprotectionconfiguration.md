<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10endpointprotectionconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# windows10EndpointProtectionConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the Windows10EndpointProtectionConfiguration resource.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows10EndpointProtectionConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10endpointprotectionconfiguration-list?view=graph-rest-1.0) | [windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10endpointprotectionconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10endpointprotectionconfiguration?view=graph-rest-1.0) objects. |
| [Get windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10endpointprotectionconfiguration-get?view=graph-rest-1.0) | [windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10endpointprotectionconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10endpointprotectionconfiguration?view=graph-rest-1.0) object. |
| [Create windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10endpointprotectionconfiguration-create?view=graph-rest-1.0) | [windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10endpointprotectionconfiguration?view=graph-rest-1.0) | Create a new [windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10endpointprotectionconfiguration?view=graph-rest-1.0) object. |
| [Delete windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10endpointprotectionconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10endpointprotectionconfiguration?view=graph-rest-1.0). |
| [Update windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10endpointprotectionconfiguration-update?view=graph-rest-1.0) | [windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10endpointprotectionconfiguration?view=graph-rest-1.0) | Update the properties of a [windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10endpointprotectionconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| applicationGuardEnabled | Boolean | Enable Windows Defender Application Guard |
| applicationGuardBlockFileTransfer | [applicationGuardBlockFileTransferType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applicationguardblockfiletransfertype?view=graph-rest-1.0) | Block clipboard to transfer image file, text file or neither of them. The possible values are: `notConfigured`, `blockImageAndTextFile`, `blockImageFile`, `blockNone`, `blockTextFile`. |
| applicationGuardBlockNonEnterpriseContent | Boolean | Block enterprise sites to load non-enterprise content, such as third party plug-ins |
| applicationGuardAllowPersistence | Boolean | Allow persisting user generated data inside the App Guard Containter \(favorites, cookies, web passwords, etc.\) |
| applicationGuardForceAuditing | Boolean | Force auditing will persist Windows logs and events to meet security/compliance criteria \(sample events are user login-logoff, use of privilege rights, software installation, system changes, etc.\) |
| applicationGuardBlockClipboardSharing | [applicationGuardBlockClipboardSharingType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applicationguardblockclipboardsharingtype?view=graph-rest-1.0) | Block clipboard to share data from Host to Container, or from Container to Host, or both ways, or neither ways. The possible values are: `notConfigured`, `blockBoth`, `blockHostToContainer`, `blockContainerToHost`, `blockNone`. |
| applicationGuardAllowPrintToPDF | Boolean | Allow printing to PDF from Container |
| applicationGuardAllowPrintToXPS | Boolean | Allow printing to XPS from Container |
| applicationGuardAllowPrintToLocalPrinters | Boolean | Allow printing to Local Printers from Container |
| applicationGuardAllowPrintToNetworkPrinters | Boolean | Allow printing to Network Printers from Container |
| appLockerApplicationControl | [appLockerApplicationControlType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applockerapplicationcontroltype?view=graph-rest-1.0) | Enables the Admin to choose what types of app to allow on devices. The possible values are: `notConfigured`, `enforceComponentsAndStoreApps`, `auditComponentsAndStoreApps`, `enforceComponentsStoreAppsAndSmartlocker`, `auditComponentsStoreAppsAndSmartlocker`. |
| bitLockerDisableWarningForOtherDiskEncryption | Boolean | Allows the Admin to disable the warning prompt for other disk encryption on the user machines. |
| bitLockerEnableStorageCardEncryptionOnMobile | Boolean | Allows the admin to require encryption to be turned on using BitLocker. This policy is valid only for a mobile SKU. |
| bitLockerEncryptDevice | Boolean | Allows the admin to require encryption to be turned on using BitLocker. |
| bitLockerRemovableDrivePolicy | [bitLockerRemovableDrivePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-bitlockerremovabledrivepolicy?view=graph-rest-1.0) | BitLocker Removable Drive Policy. |
| defenderAttackSurfaceReductionExcludedPaths | String collection | List of exe files and folders to be excluded from attack surface reduction rules |
| defenderGuardedFoldersAllowedAppPaths | String collection | List of paths to exe that are allowed to access protected folders |
| defenderAdditionalGuardedFolders | String collection | List of folder paths to be added to the list of protected folders |
| defenderExploitProtectionXml | Binary | Xml content containing information regarding exploit protection details. |
| defenderExploitProtectionXmlFileName | String | Name of the file from which DefenderExploitProtectionXml was obtained. |
| defenderSecurityCenterBlockExploitProtectionOverride | Boolean | Indicates whether or not to block user from overriding Exploit Protection settings. |
| firewallBlockStatefulFTP | Boolean | Blocks stateful FTP connections to the device |
| firewallIdleTimeoutForSecurityAssociationInSeconds | Int32 | Configures the idle timeout for security associations, in seconds, from 300 to 3600 inclusive. This is the period after which security associations will expire and be deleted. Valid values 300 to 3600 |
| firewallPreSharedKeyEncodingMethod | [firewallPreSharedKeyEncodingMethodType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-firewallpresharedkeyencodingmethodtype?view=graph-rest-1.0) | Select the preshared key encoding to be used. The possible values are: `deviceDefault`, `none`, `utF8`. |
| firewallIPSecExemptionsAllowNeighborDiscovery | Boolean | Configures IPSec exemptions to allow neighbor discovery IPv6 ICMP type-codes |
| firewallIPSecExemptionsAllowICMP | Boolean | Configures IPSec exemptions to allow ICMP |
| firewallIPSecExemptionsAllowRouterDiscovery | Boolean | Configures IPSec exemptions to allow router discovery IPv6 ICMP type-codes |
| firewallIPSecExemptionsAllowDHCP | Boolean | Configures IPSec exemptions to allow both IPv4 and IPv6 DHCP traffic |
| firewallCertificateRevocationListCheckMethod | [firewallCertificateRevocationListCheckMethodType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-firewallcertificaterevocationlistcheckmethodtype?view=graph-rest-1.0) | Specify how the certificate revocation list is to be enforced. The possible values are: `deviceDefault`, `none`, `attempt`, `require`. |
| firewallMergeKeyingModuleSettings | Boolean | If an authentication set is not fully supported by a keying module, direct the module to ignore only unsupported authentication suites rather than the entire set |
| firewallPacketQueueingMethod | [firewallPacketQueueingMethodType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-firewallpacketqueueingmethodtype?view=graph-rest-1.0) | Configures how packet queueing should be applied in the tunnel gateway scenario. The possible values are: `deviceDefault`, `disabled`, `queueInbound`, `queueOutbound`, `queueBoth`. |
| firewallProfileDomain | [windowsFirewallNetworkProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsfirewallnetworkprofile?view=graph-rest-1.0) | Configures the firewall profile settings for domain networks |
| firewallProfilePublic | [windowsFirewallNetworkProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsfirewallnetworkprofile?view=graph-rest-1.0) | Configures the firewall profile settings for public networks |
| firewallProfilePrivate | [windowsFirewallNetworkProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsfirewallnetworkprofile?view=graph-rest-1.0) | Configures the firewall profile settings for private networks |
| smartScreenEnableInShell | Boolean | Allows IT Admins to configure SmartScreen for Windows. |
| smartScreenBlockOverrideForFiles | Boolean | Allows IT Admins to control whether users can can ignore SmartScreen warnings and run malicious files. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) collection | The list of assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceStatuses | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) collection | Device configuration installation status by device. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| userStatuses | [deviceConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatus?view=graph-rest-1.0) collection | Device configuration installation status by user. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceStatusOverview | [deviceConfigurationDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdeviceoverview?view=graph-rest-1.0) | Device Configuration devices status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| userStatusOverview | [deviceConfigurationUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuseroverview?view=graph-rest-1.0) | Device Configuration users status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceSettingStateSummaries | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) collection | Device Configuration Setting State Device Summary Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windows10EndpointProtectionConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "applicationGuardEnabled": true,
  "applicationGuardBlockFileTransfer": "String",
  "applicationGuardBlockNonEnterpriseContent": true,
  "applicationGuardAllowPersistence": true,
  "applicationGuardForceAuditing": true,
  "applicationGuardBlockClipboardSharing": "String",
  "applicationGuardAllowPrintToPDF": true,
  "applicationGuardAllowPrintToXPS": true,
  "applicationGuardAllowPrintToLocalPrinters": true,
  "applicationGuardAllowPrintToNetworkPrinters": true,
  "appLockerApplicationControl": "String",
  "bitLockerDisableWarningForOtherDiskEncryption": true,
  "bitLockerEnableStorageCardEncryptionOnMobile": true,
  "bitLockerEncryptDevice": true,
  "bitLockerRemovableDrivePolicy": {
    "@odata.type": "microsoft.graph.bitLockerRemovableDrivePolicy",
    "encryptionMethod": "String",
    "requireEncryptionForWriteAccess": true,
    "blockCrossOrganizationWriteAccess": true
  },
  "defenderAttackSurfaceReductionExcludedPaths": [
    "String"
  ],
  "defenderGuardedFoldersAllowedAppPaths": [
    "String"
  ],
  "defenderAdditionalGuardedFolders": [
    "String"
  ],
  "defenderExploitProtectionXml": "binary",
  "defenderExploitProtectionXmlFileName": "String",
  "defenderSecurityCenterBlockExploitProtectionOverride": true,
  "firewallBlockStatefulFTP": true,
  "firewallIdleTimeoutForSecurityAssociationInSeconds": 1024,
  "firewallPreSharedKeyEncodingMethod": "String",
  "firewallIPSecExemptionsAllowNeighborDiscovery": true,
  "firewallIPSecExemptionsAllowICMP": true,
  "firewallIPSecExemptionsAllowRouterDiscovery": true,
  "firewallIPSecExemptionsAllowDHCP": true,
  "firewallCertificateRevocationListCheckMethod": "String",
  "firewallMergeKeyingModuleSettings": true,
  "firewallPacketQueueingMethod": "String",
  "firewallProfileDomain": {
    "@odata.type": "microsoft.graph.windowsFirewallNetworkProfile",
    "firewallEnabled": "String",
    "stealthModeBlocked": true,
    "incomingTrafficBlocked": true,
    "unicastResponsesToMulticastBroadcastsBlocked": true,
    "inboundNotificationsBlocked": true,
    "authorizedApplicationRulesFromGroupPolicyMerged": true,
    "globalPortRulesFromGroupPolicyMerged": true,
    "connectionSecurityRulesFromGroupPolicyMerged": true,
    "outboundConnectionsBlocked": true,
    "inboundConnectionsBlocked": true,
    "securedPacketExemptionAllowed": true,
    "policyRulesFromGroupPolicyMerged": true
  },
  "firewallProfilePublic": {
    "@odata.type": "microsoft.graph.windowsFirewallNetworkProfile",
    "firewallEnabled": "String",
    "stealthModeBlocked": true,
    "incomingTrafficBlocked": true,
    "unicastResponsesToMulticastBroadcastsBlocked": true,
    "inboundNotificationsBlocked": true,
    "authorizedApplicationRulesFromGroupPolicyMerged": true,
    "globalPortRulesFromGroupPolicyMerged": true,
    "connectionSecurityRulesFromGroupPolicyMerged": true,
    "outboundConnectionsBlocked": true,
    "inboundConnectionsBlocked": true,
    "securedPacketExemptionAllowed": true,
    "policyRulesFromGroupPolicyMerged": true
  },
  "firewallProfilePrivate": {
    "@odata.type": "microsoft.graph.windowsFirewallNetworkProfile",
    "firewallEnabled": "String",
    "stealthModeBlocked": true,
    "incomingTrafficBlocked": true,
    "unicastResponsesToMulticastBroadcastsBlocked": true,
    "inboundNotificationsBlocked": true,
    "authorizedApplicationRulesFromGroupPolicyMerged": true,
    "globalPortRulesFromGroupPolicyMerged": true,
    "connectionSecurityRulesFromGroupPolicyMerged": true,
    "outboundConnectionsBlocked": true,
    "inboundConnectionsBlocked": true,
    "securedPacketExemptionAllowed": true,
    "policyRulesFromGroupPolicyMerged": true
  },
  "smartScreenEnableInShell": true,
  "smartScreenBlockOverrideForFiles": true
}
```
