<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosendpointprotectionconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# macOSEndpointProtectionConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

MacOS endpoint protection configuration profile.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSEndpointProtectionConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosendpointprotectionconfiguration-list?view=graph-rest-beta) | [macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosendpointprotectionconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosendpointprotectionconfiguration?view=graph-rest-beta) objects. |
| [Get macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosendpointprotectionconfiguration-get?view=graph-rest-beta) | [macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosendpointprotectionconfiguration?view=graph-rest-beta) | Read properties and relationships of the [macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosendpointprotectionconfiguration?view=graph-rest-beta) object. |
| [Create macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosendpointprotectionconfiguration-create?view=graph-rest-beta) | [macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosendpointprotectionconfiguration?view=graph-rest-beta) | Create a new [macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosendpointprotectionconfiguration?view=graph-rest-beta) object. |
| [Delete macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosendpointprotectionconfiguration-delete?view=graph-rest-beta) | None | Deletes a [macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosendpointprotectionconfiguration?view=graph-rest-beta). |
| [Update macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosendpointprotectionconfiguration-update?view=graph-rest-beta) | [macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosendpointprotectionconfiguration?view=graph-rest-beta) | Update the properties of a [macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosendpointprotectionconfiguration?view=graph-rest-beta) object. |

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
| gatekeeperAllowedAppSource | [macOSGatekeeperAppSources](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgatekeeperappsources?view=graph-rest-beta) | System and Privacy setting that determines which download locations apps can be run from on a macOS device. Possible values are: `notConfigured`, `macAppStore`, `macAppStoreAndIdentifiedDevelopers`, `anywhere`. |
| gatekeeperBlockOverride | Boolean | If set to true, the user override for Gatekeeper will be disabled. |
| firewallEnabled | Boolean | Whether the firewall should be enabled or not. |
| firewallBlockAllIncoming | Boolean | Corresponds to the “Block all incoming connections” option. |
| firewallEnableStealthMode | Boolean | Corresponds to “Enable stealth mode.” |
| firewallApplications | [macOSFirewallApplication](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosfirewallapplication?view=graph-rest-beta) collection | List of applications with firewall settings. Firewall settings for applications not on this list are determined by the user. This collection can contain a maximum of 500 elements. |
| fileVaultEnabled | Boolean | Whether FileVault should be enabled or not. |
| fileVaultSelectedRecoveryKeyTypes | [macOSFileVaultRecoveryKeyTypes](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosfilevaultrecoverykeytypes?view=graph-rest-beta) | Required if FileVault is enabled, determines the type\(s\) of recovery key to use. . Possible values are: `notConfigured`, `institutionalRecoveryKey`, `personalRecoveryKey`. |
| fileVaultInstitutionalRecoveryKeyCertificate | Binary | Required if selected recovery key type\(s\) include InstitutionalRecoveryKey. The DER Encoded certificate file used to set an institutional recovery key. |
| fileVaultInstitutionalRecoveryKeyCertificateFileName | String | File name of the institutional recovery key certificate to display in UI. \(\*.der\). |
| fileVaultPersonalRecoveryKeyHelpMessage | String | Required if selected recovery key type\(s\) include PersonalRecoveryKey. A short message displayed to the user that explains how they can retrieve their personal recovery key. |
| fileVaultAllowDeferralUntilSignOut | Boolean | Optional. If set to true, the user can defer the enabling of FileVault until they sign out. |
| fileVaultNumberOfTimesUserCanIgnore | Int32 | Optional. When using the Defer option, this is the maximum number of times the user can ignore prompts to enable FileVault before FileVault will be required for the user to sign in. If set to -1, it will always prompt to enable FileVault until FileVault is enabled, though it will allow the user to bypass enabling FileVault. Setting this to 0 will disable the feature. |
| fileVaultDisablePromptAtSignOut | Boolean | Optional. When using the Defer option, if set to true, the user is not prompted to enable FileVault at sign-out. |
| fileVaultPersonalRecoveryKeyRotationInMonths | Int32 | Optional. If selected recovery key type\(s\) include PersonalRecoveryKey, the frequency to rotate that key, in months. |
| fileVaultHidePersonalRecoveryKey | Boolean | Optional. A hidden personal recovery key does not appear on the user's screen during FileVault encryption, reducing the risk of it ending up in the wrong hands. |
| advancedThreatProtectionRealTime | [enablement](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enablement?view=graph-rest-beta) | Determines whether or not to enable real-time protection for Microsoft Defender Advanced Threat Protection on macOS. Possible values are: `notConfigured`, `enabled`, `disabled`. |
| advancedThreatProtectionCloudDelivered | [enablement](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enablement?view=graph-rest-beta) | Determines whether or not to enable cloud-delivered protection for Microsoft Defender Advanced Threat Protection on macOS. Possible values are: `notConfigured`, `enabled`, `disabled`. |
| advancedThreatProtectionAutomaticSampleSubmission | [enablement](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enablement?view=graph-rest-beta) | Determines whether or not to enable automatic file sample submission for Microsoft Defender Advanced Threat Protection on macOS. Possible values are: `notConfigured`, `enabled`, `disabled`. |
| advancedThreatProtectionDiagnosticDataCollection | [enablement](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enablement?view=graph-rest-beta) | Determines whether or not to enable diagnostic and usage data collection for Microsoft Defender Advanced Threat Protection on macOS. Possible values are: `notConfigured`, `enabled`, `disabled`. |
| advancedThreatProtectionExcludedFolders | String collection | A list of paths to folders to exclude from antivirus scanning for Microsoft Defender Advanced Threat Protection on macOS. |
| advancedThreatProtectionExcludedFiles | String collection | A list of paths to files to exclude from antivirus scanning for Microsoft Defender Advanced Threat Protection on macOS. |
| advancedThreatProtectionExcludedExtensions | String collection | A list of file extensions to exclude from antivirus scanning for Microsoft Defender Advanced Threat Protection on macOS. |
| advancedThreatProtectionExcludedProcesses | String collection | A list of process names to exclude from antivirus scanning for Microsoft Defender Advanced Threat Protection on macOS. |

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
  "@odata.type": "#microsoft.graph.macOSEndpointProtectionConfiguration",
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
  "gatekeeperAllowedAppSource": "String",
  "gatekeeperBlockOverride": true,
  "firewallEnabled": true,
  "firewallBlockAllIncoming": true,
  "firewallEnableStealthMode": true,
  "firewallApplications": [
    {
      "@odata.type": "microsoft.graph.macOSFirewallApplication",
      "bundleId": "String",
      "allowsIncomingConnections": true
    }
  ],
  "fileVaultEnabled": true,
  "fileVaultSelectedRecoveryKeyTypes": "String",
  "fileVaultInstitutionalRecoveryKeyCertificate": "binary",
  "fileVaultInstitutionalRecoveryKeyCertificateFileName": "String",
  "fileVaultPersonalRecoveryKeyHelpMessage": "String",
  "fileVaultAllowDeferralUntilSignOut": true,
  "fileVaultNumberOfTimesUserCanIgnore": 1024,
  "fileVaultDisablePromptAtSignOut": true,
  "fileVaultPersonalRecoveryKeyRotationInMonths": 1024,
  "fileVaultHidePersonalRecoveryKey": true,
  "advancedThreatProtectionRealTime": "String",
  "advancedThreatProtectionCloudDelivered": "String",
  "advancedThreatProtectionAutomaticSampleSubmission": "String",
  "advancedThreatProtectionDiagnosticDataCollection": "String",
  "advancedThreatProtectionExcludedFolders": [
    "String"
  ],
  "advancedThreatProtectionExcludedFiles": [
    "String"
  ],
  "advancedThreatProtectionExcludedExtensions": [
    "String"
  ],
  "advancedThreatProtectionExcludedProcesses": [
    "String"
  ]
}
```
