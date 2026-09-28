<!-- Source: https://learn.microsoft.com/en-us/graph/utcm-intune-resources -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# Supported Microsoft Intune resources for Tenant Configuration Management

This article lists the supported resource types for Microsoft Intune in the Tenant Configuration Management \(TCM\) APIs in Microsoft Graph. Use these resource types to monitor and manage your Microsoft Intune configuration settings.

For the complete schema, required permissions, and examples for each resource type, see the [TCM schema store](https://json.schemastore.org/utcm-monitor.json).

## accountProtectionLocalUserGroupMembershipPolicy resource type

### Description

This resource configures a Intune Account Protection Local User Group Membership policy.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Write | String | Identity of the account protection policy. | - |
| DisplayName | Key | String | Display name of the account protection rules policy. | - |
| Description | Write | String | Description of the account protection rules policy. | - |
| Assignments | Write | AccountProtectionLocalUserGroupMembershipPolicyAssignments\[\] | Assignments of the Intune Policy. | - |
| LocalUserGroupCollection | Write | AccountProtectionLocalUserGroupCollection\[\] | Local User Group Collections of the Intune Policy. | - |
| Ensure | Write | String | Present ensures the site collection exists, absent ensures it's removed | `Present`, `Absent` |

#### AccountProtectionLocalUserGroupMembershipPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### AccountProtectionLocalUserGroupCollection

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Action | Write | String | The action to use for adding / removing members. | `add_update`, `remove_update`, `add_replace` |
| LocalGroups | Write | StringArray\[\] | The local groups to add / remove the members to / from. List of the following values: `administrators`, `users`, `guests`, `powerusers`, `remotedesktopusers`, `remotemanagementusers` | - |
| Members | Write | StringArray\[\] | The members to add / remove to / from the group. For AzureAD Users, use the format `AzureAD\\&lt;UserPrincipalName&gt;`. For groups, use the security identifier \(SID\). | - |
| UserSelectionType | Write | String | The type of the selection. Either users / groups from AzureAD, or by manual identifier. | `users`, `manual` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## accountProtectionPolicy resource type

### Description

This resource configures a Intune Account Protection policy.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Write | String | Identity of the account protection policy. | - |
| DisplayName | Key | String | Display name of the account protection rules policy. | - |
| Description | Write | String | Description of the account protection rules policy. | - |
| Assignments | Write | AccountProtectionPolicyAssignments\[\] | Assignments of the Intune Policy. | - |
| WindowsHelloForBusinessBlocked | Write | String | Block Windows Hello for Business. | `notConfigured`, `true`, `false` |
| PinMinimumLength | Write | UInt32 | Minimum PIN length must be between 4 and 127. \(4-127\) | - |
| PinMaximumLength | Write | UInt32 | Maximum PIN length must be between 4 and 127. \(4-127\) | - |
| PinLowercaseCharactersUsage | Write | String | If required, user PIN must include at least one lowercase letter. | `notConfigured`, `blocked`, `required`, `allowed` |
| PinUppercaseCharactersUsage | Write | String | If required, user PIN must include at least one uppercase letter. | `notConfigured`, `blocked`, `required`, `allowed` |
| PinSpecialCharactersUsage | Write | String | If required, user PIN must include at least one special character. | `notConfigured`, `blocked`, `required`, `allowed` |
| PinExpirationInDays | Write | UInt32 | If configured, the user will be forced to change their PIN after the set number of days. \(0, 730\), 0 = Never | - |
| PinPreviousBlockCount | Write | UInt32 | If configured, the user will not be able to reuse this number of previous PINs. \(0, 50\), 0 = Do not remember. | - |
| PinRecoveryEnabled | Write | Boolean | If enabled, the PIN recovery secret will be stored on the device and the user can change their PIN if needed. If disabled or not configured, the recovery secret will not be created or stored. | - |
| SecurityDeviceRequired | Write | Boolean | If you enable this policy setting, only devices with a usable TPM provision Windows Hello for Business. If you disable or do not configure this policy setting, the TPM is still preferred, but all devices provision Windows Hello for Business. | - |
| UnlockWithBiometricsEnabled | Write | Boolean | If allowed, Windows Hello for Business can authenticate using gestures, such as face and fingerprint. Users must still configure a PIN in case of failure. | - |
| EnhancedAntiSpoofingForFacialFeaturesEnabled | Write | Boolean | If enabled, devices will use enhanced anti-spoofing, when available. If not configured, the client configuration for anti-spoofing will be honored. | - |
| UseCertificatesForOnPremisesAuthEnabled | Write | Boolean | If configured, Windows Hello for Business can use certificates to authenticate to on-premise resources. | - |
| UseSecurityKeyForSignin | Write | Boolean | Enable Windows Hello security key as a logon credential for all PCs in the tenant. | - |
| DeviceGuardLocalSystemAuthorityCredentialGuardSettings | Write | String | Setting this Disable will disable the use of Credential Guard, which is the Windows default. Setting this to Enable with UEFI lock will enable Credential Guard and not allow it to be disabled remotely, as the UEFI persisted configuration must be manually cleared. Setting this to Enable without UEFI lock will enable Credential Guard and allow it to be turned off without physical access to the machine. | `notConfigured`, `disable`, `enableWithUEFILock`, `enableWithoutUEFILock` |
| Ensure | Write | String | Present ensures the site collection exists, absent ensures it's removed | `Present`, `Absent` |

#### AccountProtectionPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | DeviceManagementConfiguration.ReadWrite.All |

## antivirusPolicyWindows10SettingCatalog resource type

### Description

This resource configures an Intune Endpoint Protection Antivirus policy for a Windows 10 Device. This policy setting enables the management of Microsoft Defender Antivirus for Windows 10 using the settings catalog.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the endpoint protection policy for Windows 10. | - |
| Identity | Write | String | Identity of the endpoint protection policy for Windows 10. | - |
| Description | Write | String | Description of the endpoint protection policy for Windows 10. | - |
| tamperprotection | Write | String | Allows or disallows scanning of archives. \(0: enable feature. 1: disable feature\) | `0`, `1` |
| disableaccountprotectionui | Write | String | Use this policy setting to specify if to display the Account protection area in Windows Defender Security Center. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| disableappbrowserui | Write | String | Use this policy setting if you want to disable the display of the app and browser protection area in Windows Defender Security Center. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| disablecleartpmbutton | Write | String | Disable the Clear TPM button in Windows Security. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| disabledevicesecurityui | Write | String | Use this policy setting if you want to disable the display of the Device security area in the Windows Defender Security Center. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| disablefamilyui | Write | String | Use this policy setting if you want to disable the display of the family options area in Windows Defender Security Center. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| disablehealthui | Write | String | Use this policy setting if you want to disable the display of the device performance and health area in Windows Defender Security Center. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| disablenetworkui | Write | String | Use this policy setting if you want to disable the display of the firewall and network protection area in Windows Defender Security Center. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| disableenhancednotifications | Write | String | Use this policy setting if you want to disable the display of Windows Defender Security Center notifications. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| disabletpmfirmwareupdatewarning | Write | String | Hide the recommendation to update TPM Firmware when a vulnerable firmware is detected. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| disablevirusui | Write | String | Use this policy setting if you want to disable the display of the virus and threat protection area in Windows Defender Security Center. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| hideransomwaredatarecovery | Write | String | Use this policy setting to hide the Ransomware data recovery area in Windows Defender Security Center. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| hidewindowssecuritynotificationareacontrol | Write | String | This policy setting hides the Windows Security notification area control. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| enablecustomizedtoasts | Write | String | Enable this policy to display your company name and contact options in the notifications. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| enableinappcustomization | Write | String | Enable this policy to have your company name and contact options displayed in a contact card fly out in Windows Defender Security Center. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| companyname | Write | String | The company name that is displayed to the users. CompanyName is required for both EnableCustomizedToasts and EnableInAppCustomization. | - |
| email | Write | String | The email address that is displayed to users. The default mail application is used to initiate email actions. | - |
| phone | Write | String | The phone number or Skype ID that is displayed to users. Skype is used to initiate the call. | - |
| url | Write | String | The help portal URL that is displayed to users. The default browser is used to initiate this action. | - |
| allowarchivescanning | Write | String | Allows or disallows scanning of archives. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowbehaviormonitoring | Write | String | Allows or disallows Windows Defender Behavior Monitoring functionality. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowcloudprotection | Write | String | To best protect your PC, Windows Defender will send information to Microsoft about any problems it finds. Microsoft will analyze that information, learn more about problems affecting you and other customers, and offer improved solutions. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowdatagramprocessingonwinserver | Write | String | Allows or disallows Network Protection to enable datagram processing on Windows Server. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowemailscanning | Write | String | Allows or disallows scanning of email. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowfullscanonmappednetworkdrives | Write | String | Allows or disallows a full scan of mapped network drives. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowfullscanremovabledrivescanning | Write | String | Allows or disallows a full scan of removable drives. During a quick scan, removable drives may still be scanned. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowintrusionpreventionsystem | Write | String | [https://github.com/MicrosoftDocs/memdocs/issues/2250](https://github.com/MicrosoftDocs/memdocs/issues/2250) \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowioavprotection | Write | String | Allows or disallows Windows Defender IOAVP Protection functionality. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allownetworkprotectiondownlevel | Write | String | Allows or disallows Network Protection to be configured into block or audit mode on windows downlevel of RS3. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowrealtimemonitoring | Write | String | Allows or disallows Windows Defender real-time Monitoring functionality. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowscanningnetworkfiles | Write | String | Allows or disallows a scanning of network files. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowscriptscanning | Write | String | Allows or disallows Windows Defender Script Scanning functionality. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| allowuseruiaccess | Write | String | Allows or disallows user access to the Windows Defender UI. I disallowed, all Windows Defender notifications will also be suppressed. \(0: Prevents users from accessing UI. 1: Lets users access UI\) | `0`, `1` |
| avgcpuloadfactor | Write | SInt32 | Represents the average CPU load factor for the Windows Defender scan \(in percent\). | - |
| archivemaxdepth | Write | SInt32 | Specify the maximum folder depth to extract from archive files for scanning. | - |
| archivemaxsize | Write | SInt32 | Specify the maximum size, in KB, of archive files to be extracted and scanned. | - |
| checkforsignaturesbeforerunningscan | Write | String | This policy setting allows you to manage whether a check for new virus and spyware definitions will occur before running a scan. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| cloudblocklevel | Write | String | This policy setting determines how aggressive Microsoft Defender Antivirus will be in blocking and scanning suspicious files. Value type is integer.\(0: Default windows defender blocking level, 2: High blocking level, 4:High+ blocking level, 6:Zero tolerance blocking level\) | `0`, `2`, `4`, `6` |
| cloudextendedtimeout | Write | SInt32 | This feature allows Microsoft Defender Antivirus to block a suspicious file for up to 60 seconds, and scan it in the cloud to make sure it's safe. Value type is integer, range is 0 - 50. | - |
| daystoretaincleanedmalware | Write | SInt32 | Time period \(in days\) that quarantine items will be stored on the system. | - |
| disablecatchupfullscan | Write | String | This policy setting allows you to configure catch-up scans for scheduled full scans. \(1: disabled, 0: enabled\) | `0`, `1` |
| disablecatchupquickscan | Write | String | This policy setting allows you to configure catch-up scans for scheduled quick scans. \(1: disabled, 0: enabled\) | `0`, `1` |
| disablednsovertcpparsing | Write | String | Disables or enables DNS over TCP Parsing for Network Protection. \(0: enable feature. 1: disable feature\) | `0`, `1` |
| disablehttpparsing | Write | String | Disables or enables HTTP Parsing for Network Protection. \(0: enable feature. 1: disable feature\) | `0`, `1` |
| DisableSshParsing | Write | String | Disable Ssh Parsing \(1: SSH parsing is disabled, 0: SSH parsing is enabled\) | `1`, `0` |
| enablelowcpupriority | Write | String | This policy setting allows you to enable or disable low CPU priority for scheduled scans. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| enablenetworkprotection | Write | String | This policy allows you to turn on network protection \(block/audit\) or off. \(0: disabled, 1: block mode, 2: audit mode\) | `0`, `1`, `2` |
| excludedextensions | Write | StringArray\[\] | Allows an administrator to specify a list of file type extensions to ignore during a scan. | - |
| excludedpaths | Write | StringArray\[\] | Allows an administrator to specify a list of directory paths to ignore during a scan. | - |
| excludedprocesses | Write | StringArray\[\] | Allows an administrator to specify a list of files opened by processes to ignore during a scan. | - |
| puaprotection | Write | String | Specifies the level of detection for potentially unwanted applications \(PUAs\). \(0: disabled, 1: block mode, 2: audit mode\) | `0`, `1`, `2` |
| engineupdateschannel | Write | String | Enable this policy to specify when devices receive Microsoft Defender engine updates during the monthly gradual rollout. \(0: Not configured, 2: Beta Channel, 3: Current Channel \(Preview\), 4: Current Channel \(Staged\), 5: Current Channel \(Broad\), 6: Critical\) | `0`, `2`, `3`, `4`, `5`, `6` |
| meteredconnectionupdates | Write | String | Allow managed devices to update through metered connections. \(0: disabled, 1: enabled\) | - |
| platformupdateschannel | Write | String | Enable this policy to specify when devices receive Microsoft Defender platform updates during the monthly gradual rollout. \(0: Not configured, 2: Beta Channel, 3: Current Channel \(Preview\), 4: Current Channel \(Staged\), 5: Current Channel \(Broad\), 6: Critical\) | `0`, `2`, `3`, `4`, `5`, `6` |
| securityintelligenceupdateschannel | Write | String | Enable this policy to specify when devices receive Microsoft Defender security intelligence updates during the daily gradual rollout. \(0: Not configured, 4: Current Channel \(Staged\), 5: Current Channel \(Broad\)\) | `0`, `4`, `5` |
| realtimescandirection | Write | String | Controls which sets of files should be monitored. \(0: Monitor all files \(bi-directional\), 1: Monitor incoming files, 2: Monitor outgoing files\) | `0`, `1`, `2` |
| scanparameter | Write | String | Selects whether to perform a quick scan or full scan. \(1: Quick scan, 2: Full scan\) | `1`, `2` |
| schedulequickscantime | Write | SInt32 | Selects the time of day that the Windows Defender quick scan should run. | - |
| schedulescanday | Write | String | Selects the day that the Windows Defender scan should run. \(0: Every day, 1: Sunday, 2: Monday, 3: Tuesday, 4: Wednesday, 5: Thursday, 6: Friday, 7: Saturday, 8: No scheduled scan\) | `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8` |
| schedulescantime | Write | SInt32 | Selects the time of day that the Windows Defender scan should run. Must be between 0 and 1380 minutes. | - |
| disabletlsparsing | Write | String | This setting disables TLS Parsing for Network Protection. \(0: enabled, 1: disabled\) | `0`, `1` |
| randomizescheduletasktimes | Write | String | Specifies if the start time of the scan is randomized. \(0: no randomization, 1: randomized\) | `0`, `1` |
| schedulerrandomizationtime | Write | SInt32 | This setting allows you to configure the scheduler randomization in hours. The randomization interval is \[1 - 23\] hours. | - |
| signatureupdatefallbackorder | Write | StringArray\[\] | This policy setting allows you to define the order in which different definition update sources should be contacted. | - |
| signatureupdatefilesharessources | Write | StringArray\[\] | This policy setting allows you to configure UNC file share sources for downloading definition updates. | - |
| signatureupdateinterval | Write | SInt32 | Specifies the interval \(in hours\) that will be used to check for signatures, so instead of using the ScheduleDay and ScheduleTime the check for new signatures will be set according to the interval. Must be between 0 and 24 hours. | - |
| submitsamplesconsent | Write | String | Checks for the user consent level in Windows Defender to send data. \(0: Always prompt, 1: Send safe samples automatically, 2: Never send, 3: Send all samples automatically\) | `0`, `1`, `2`, `3` |
| disablelocaladminmerge | Write | String | This policy setting controls whether or not complex list settings configured by a local administrator are merged with managed settings. \(0: enable local admin merge, 1: disable local admin merge\) | `0`, `1` |
| allowonaccessprotection | Write | String | Allows or disallows Windows Defender On Access Protection functionality. \(0: disable feature. 1: enable feature\) | `0`, `1` |
| lowseveritythreats | Write | String | Allows an administrator to specify low severity threats corresponding action ID to take. | `clean`, `quarantine`, `remove`, `allow`, `userdefined`, `block` |
| moderateseveritythreats | Write | String | Allows an administrator to specify moderate severity threats corresponding action ID to take. | `clean`, `quarantine`, `remove`, `allow`, `userdefined`, `block` |
| severethreats | Write | String | Allows an administrator to specify high severity threats corresponding action ID to take. | `clean`, `quarantine`, `remove`, `allow`, `userdefined`, `block` |
| highseveritythreats | Write | String | Allows an administrator to specify severe threats corresponding action ID to take. | `clean`, `quarantine`, `remove`, `allow`, `userdefined`, `block` |
| templateId | Write | String | Template Id of the policy. 0: Windows Security Experience, 1: Defender Update controls, 2: Microsoft Defender Antivirus exclusions, 3: Microsoft Defender Antivirus | `d948ff9b-99cb-4ee0-8012-1fbc09685377_1`, `e3f74c5a-a6de-411d-aef6-eb15628f3a0a_1`, `45fea5e9-280d-4da1-9792-fb5736da0ca9_1`, `804339ad-1553-4478-a742-138fb5807418_1` |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## appConfigurationPolicy resource type

### Description

This resource configures the Intune App configuration policies.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Key of the entity. Read-Only. | - |
| DisplayName | Key | String | Display name of the app configuration policy. | - |
| Description | Write | String | Description of the app configuration policy. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the Intune Policy. | - |
| CustomSettings | Write | AppConfigurationPolicyCustomSetting\[\] | Custom settings for the app cnfiguration policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### AppConfigurationPolicyCustomSetting

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| name | Write | String | Name of the custom setting. | - |
| value | Write | String | Value of the custom setting. | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementApps.Read.All |
| Update | Group.Read.All, DeviceManagementApps.ReadWrite.All |

## applicationControlPolicyWindows10 resource type

### Description

This resource configures a Intune Endpoint Protection Application Control policy for an Windows 10 Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the endpoint protection application control policy for Windows 10. | - |
| Description | Write | String | Description of the endpoint protection application control policy for Windows 10. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the Intune Policy. | - |
| AppLockerApplicationControl | Write | String | App locker application control mode | `notConfigured`, `enforceComponentsAndStoreApps`, `auditComponentsAndStoreApps`, `enforceComponentsStoreAppsAndSmartlocker`, `auditComponentsStoreAppsAndSmartlocker` |
| SmartScreenBlockOverrideForFiles | Write | Boolean | Indicates whether or not SmartScreen will not present an option for the user to disregard the warning and run the app. | - |
| SmartScreenEnableInshell | Write | Boolean | Enforce the use of SmartScreen for all users. | - |
| Ensure | Write | String | Present ensures the site collection exists, absent ensures it's removed | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## appProtectionPolicyAndroid resource type

### Description

This resource configures an Intune app protection policy for an Android Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the Android App Protection Policy. | - |
| Description | Write | String | Description of the Android App Protection Policy. | - |
| PeriodOfflineBeforeAccessCheck | Write | String | The period after which access is checked when the device is not connected to the internet. | - |
| PeriodOnlineBeforeAccessCheck | Write | String | The period after which access is checked when the device is connected to the internet. | - |
| AllowedInboundDataTransferSources | Write | String | Sources from which data is allowed to be transferred. Possible values are: allApps, managedApps, none. | `allApps`, `managedApps`, `none` |
| AllowedOutboundDataTransferDestinations | Write | String | Destinations to which data is allowed to be transferred. Possible values are: allApps, managedApps, none. | `allApps`, `managedApps`, `none` |
| OrganizationalCredentialsRequired | Write | Boolean | Indicates whether organizational credentials are required for app use. | - |
| AllowedOutboundClipboardSharingLevel | Write | String | The level to which the clipboard may be shared between apps on the managed device. Possible values are: allApps, managedAppsWithPasteIn, managedApps, blocked. | `allApps`, `managedAppsWithPasteIn`, `managedApps`, `blocked` |
| DataBackupBlocked | Write | Boolean | Indicates whether the backup of a managed app's data is blocked. | - |
| DeviceComplianceRequired | Write | Boolean | Indicates whether device compliance is required. | - |
| ManagedBrowserToOpenLinksRequired | Write | Boolean | Indicates whether internet links should be opened in the managed browser app, or any custom browser specified by CustomBrowserProtocol \(for Android\) or CustomBrowserPackageId/CustomBrowserDisplayName \(for Android\). | - |
| SaveAsBlocked | Write | Boolean | Indicates whether users may use the Save As menu item to save a copy of protected files. | - |
| PeriodOfflineBeforeWipeIsEnforced | Write | String | The amount of time an app is allowed to remain disconnected from the internet before all managed data it's wiped. | - |
| PinRequired | Write | Boolean | Indicates whether an app-level pin is required. | - |
| DisableAppPinIfDevicePinIsSet | Write | Boolean | Indicates whether use of the app pin is required if the device pin is set. | - |
| MaximumPinRetries | Write | UInt32 | Maximum number of incorrect pin retry attempts before the managed app is either blocked or wiped. | - |
| SimplePinBlocked | Write | Boolean | Block simple PIN and require complex PIN to be set. | - |
| MinimumPinLength | Write | UInt32 | Minimum pin length required for an app-level pin if PinRequired is set to True. | - |
| PinCharacterSet | Write | String | Character set which may be used for an app-level pin if PinRequired is set to True. Possible values are: numeric, alphanumericAndSymbol. | `numeric`, `alphanumericAndSymbol` |
| AllowedDataStorageLocations | Write | StringArray\[\] | Data storage locations where a user may store managed data. | - |
| ContactSyncBlocked | Write | Boolean | Indicates whether contacts can be synced to the user's device. | - |
| PeriodBeforePinReset | Write | String | TimePeriod before the all-level pin must be reset if PinRequired is set to True. | - |
| PrintBlocked | Write | Boolean | Indicates whether printing is allowed from managed apps. | - |
| RequireClass3Biometrics | Write | Boolean | Require user to apply Class 3 Biometrics on their Android device. | - |
| RequirePinAfterBiometricChange | Write | Boolean | A PIN prompt will override biometric prompts if class 3 biometrics are updated on the device. | - |
| FingerprintBlocked | Write | Boolean | Indicates whether use of the fingerprint reader is allowed in place of a pin if PinRequired is set to True. | - |
| Apps | Write | StringArray\[\] | List of IDs representing the Android apps controlled by this protection policy. | - |
| Assignments | Write | StringArray\[\] | List of IDs of the groups assigned to this Android Protection Policy. | - |
| ExcludedGroups | Write | StringArray\[\] | List of IDs of the groups that are excluded from this Android Protection Policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |
| ManagedBrowser | Write | String | Indicates in which managed browser\(s\) that internet links should be opened. Used in conjunction with CustomBrowserPackageId, CustomBrowserDisplayName and ManagedBrowserToOpenLinksRequired. Possible values are: notConfigured, microsoftEdge. | `notConfigured`, `microsoftEdge` |
| MinimumRequiredAppVersion | Write | String | Versions less than the specified version will block the managed app from accessing company data. | - |
| MinimumRequiredOSVersion | Write | String | Versions less than the specified version will block the managed app from accessing company data. | - |
| MinimumRequiredPatchVersion | Write | String | Versions less than the specified version will block the managed app from accessing company data. | - |
| MinimumWarningAppVersion | Write | String | Versions less than the specified version will result in warning message on the managed app | - |
| MinimumWarningOSVersion | Write | String | Versions less than the specified version will result in warning message on the managed app | - |
| MinimumWarningPatchVersion | Write | String | Versions less than the specified version will result in warning message on the managed app | - |
| AppGroupType | Write | String | The apps controlled by this protection policy, overrides any values in Apps unless this value is 'selectedPublicApps'. | `allApps`, `allMicrosoftApps`, `allCoreMicrosoftApps`, `selectedPublicApps` |
| IsAssigned | Write | Boolean | Indicates if the policy is deployed to any inclusion groups or not. Inherited from targetedManagedAppProtection. | - |
| ScreenCaptureBlocked | Write | Boolean | Indicates whether or not to Block the user from taking Screenshots. | - |
| EncryptAppData | Write | Boolean | Indicates whether or not the 'Encrypt org data' value is enabled. True = require | - |
| DisableAppEncryptionIfDeviceEncryptionIsEnabled | Write | Boolean | Indicates whether or not the 'Encrypt org data on enrolled devices' value is enabled. False = require. Only functions if EncryptAppData is set to True | - |
| CustomBrowserDisplayName | Write | String | The application name for browser associated with the 'Unmanaged Browser ID'. This name will be displayed to users if the specified browser is not installed. | - |
| CustomBrowserPackageId | Write | String | The application ID for a single browser. Web content \(http/s\) from policy managed applications will open in the specified browser. | - |
| Id | Write | String | Id of the Intune policy. To avoid creation of duplicate policies DisplayName will be searched for if the ID is not found | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementApps.Read.All |
| Update | Group.Read.All, DeviceManagementApps.ReadWrite.All |

## appProtectionPolicyiOS resource type

### Description

This resource configures an Intune app protection policy for an iOS Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the iOS App Protection Policy. | - |
| Identity | Write | String | Identity of the iOS App Protection Policy. | - |
| Description | Write | String | Description of the iOS App Protection Policy. | - |
| PeriodOfflineBeforeAccessCheck | Write | String | The period after which access is checked when the device is not connected to the internet. | - |
| PeriodOnlineBeforeAccessCheck | Write | String | The period after which access is checked when the device is connected to the internet. | - |
| AllowedInboundDataTransferSources | Write | String | Sources from which data is allowed to be transferred. Possible values are: allApps, managedApps, none. | `allApps`, `managedApps`, `none` |
| AllowedOutboundDataTransferDestinations | Write | String | Destinations to which data is allowed to be transferred. Possible values are: allApps, managedApps, none. | `allApps`, `managedApps`, `none` |
| OrganizationalCredentialsRequired | Write | Boolean | Indicates whether organizational credentials are required for app use. | - |
| AllowedOutboundClipboardSharingLevel | Write | String | The level to which the clipboard may be shared between apps on the managed device. Possible values are: allApps, managedAppsWithPasteIn, managedApps, blocked. | `allApps`, `managedAppsWithPasteIn`, `managedApps`, `blocked` |
| DataBackupBlocked | Write | Boolean | Indicates whether the backup of a managed app's data is blocked. | - |
| DeviceComplianceRequired | Write | Boolean | Indicates whether device compliance is required. | - |
| ManagedBrowserToOpenLinksRequired | Write | Boolean | Indicates whether internet links should be opened in the managed browser app, or any custom browser specified by CustomBrowserProtocol \(for iOS\) or CustomBrowserPackageId/CustomBrowserDisplayName \(for Android\). | - |
| SaveAsBlocked | Write | Boolean | Indicates whether users may use the Save As menu item to save a copy of protected files. | - |
| PeriodOfflineBeforeWipeIsEnforced | Write | String | The amount of time an app is allowed to remain disconnected from the internet before all managed data it's wiped. | - |
| PinRequired | Write | Boolean | Indicates whether an app-level pin is required. | - |
| DisableAppPinIfDevicePinIsSet | Write | Boolean | Indicates whether use of the app pin is required if the device pin is set. | - |
| MaximumPinRetries | Write | UInt32 | Maximum number of incorrect pin retry attempts before the managed app is either blocked or wiped. | - |
| SimplePinBlocked | Write | Boolean | Block simple PIN and require complex PIN to be set. | - |
| MinimumPinLength | Write | UInt32 | Minimum pin length required for an app-level pin if PinRequired is set to True. | - |
| PinCharacterSet | Write | String | Character set which may be used for an app-level pin if PinRequired is set to True. Possible values are: numeric, alphanumericAndSymbol. | `numeric`, `alphanumericAndSymbol` |
| AllowedDataStorageLocations | Write | StringArray\[\] | Data storage locations where a user may store managed data. | - |
| ContactSyncBlocked | Write | Boolean | Indicates whether contacts can be synced to the user's device. | - |
| PeriodBeforePinReset | Write | String | TimePeriod before the all-level pin must be reset if PinRequired is set to True. | - |
| PrintBlocked | Write | Boolean | Indicates whether printing is allowed from managed apps. | - |
| FingerprintBlocked | Write | Boolean | Indicates whether use of the fingerprint reader is allowed in place of a pin if PinRequired is set to True. | - |
| FaceIdBlocked | Write | Boolean | Indicates whether use of the FaceID is allowed in place of a pin if PinRequired is set to True. | - |
| ManagedBrowser | Write | String | Indicates in which managed browser\(s\) that internet links should be opened. When this property is configured, ManagedBrowserToOpenLinksRequired should be true. Possible values are: notConfigured, microsoftEdge. | `notConfigured`, `microsoftEdge` |
| MinimumRequiredAppVersion | Write | String | Versions less than the specified version will block the managed app from accessing company data. | - |
| MinimumWarningAppVersion | Write | String | Versions less than the specified version will result in warning message on the managed app from accessing company data. | - |
| MinimumRequiredOSVersion | Write | String | Versions less than the specified version will block the managed app from accessing company data. | - |
| MinimumWarningOSVersion | Write | String | Versions less than the specified version will result in warning message on the managed app from accessing company data. | - |
| MinimumRequiredSdkVersion | Write | String | Versions less than the specified version will block the managed app from accessing company data. | - |
| MinimumWipeOSVersion | Write | String | Versions less than or equal to the specified version will wipe the managed app and the associated company data. | - |
| MinimumWipeAppVersion | Write | String | Versions less than or equal to the specified version will wipe the managed app and the associated company data. | - |
| AppActionIfDeviceComplianceRequired | Write | String | Defines a managed app behavior, either block or wipe, when the device is either rooted or jailbroken, if DeviceComplianceRequired is set to true. | `block`, `wipe`, `warn` |
| AppActionIfMaximumPinRetriesExceeded | Write | String | Defines a managed app behavior, either block or wipe, based on maximum number of incorrect pin retry attempts. | `block`, `wipe`, `warn` |
| PinRequiredInsteadOfBiometricTimeout | Write | String | Timeout in minutes for an app pin instead of non biometrics passcode . | - |
| AllowedOutboundClipboardSharingExceptionLength | Write | UInt32 | Specify the number of characters that may be cut or copied from Org data and accounts to any application. This setting overrides the AllowedOutboundClipboardSharingLevel restriction. Default value of '0' means no exception is allowed. | - |
| NotificationRestriction | Write | String | Specify app notification restriction. | `allow`, `blockOrganizationalData`, `block` |
| TargetedAppManagementLevels | Write | String | The intended app management levels for this policy. | `unspecified`, `unmanaged`, `mdm`, `androidEnterprise` |
| AppDataEncryptionType | Write | String | Require app data to be encrypted. | `useDeviceSettings`, `afterDeviceRestart`, `whenDeviceLockedExceptOpenFiles`, `whenDeviceLocked` |
| ExemptedAppProtocols | Write | StringArray\[\] | Apps in this list will be exempt from the policy and will be able to receive data from managed apps. | - |
| MinimumWipeSdkVersion | Write | String | Versions less than the specified version will block the managed app from accessing company data. | - |
| AllowedIosDeviceModels | Write | StringArray\[\] | Semicolon seperated list of device models allowed, as a string, for the managed app to work. | - |
| AppActionIfIosDeviceModelNotAllowed | Write | String | Defines a managed app behavior, either block or wipe, if the specified device model is not allowed. | `block`, `wipe`, `warn` |
| FilterOpenInToOnlyManagedApps | Write | Boolean | Defines if open-in operation is supported from the managed app to the filesharing locations selected. This setting only applies when AllowedOutboundDataTransferDestinations is set to ManagedApps and DisableProtectionOfManagedOutboundOpenInData is set to False. | - |
| DisableProtectionOfManagedOutboundOpenInData | Write | Boolean | Disable protection of data transferred to other apps through IOS OpenIn option. This setting is only allowed to be True when AllowedOutboundDataTransferDestinations is set to ManagedApps. | - |
| ProtectInboundDataFromUnknownSources | Write | Boolean | Protect incoming data from unknown source. This setting is only allowed to be True when AllowedInboundDataTransferSources is set to AllApps. | - |
| CustomBrowserProtocol | Write | String | A custom browser protocol to open weblink on iOS. | - |
| Apps | Write | StringArray\[\] | List of IDs representing the iOS apps controlled by this protection policy. | - |
| Assignments | Write | StringArray\[\] | List of IDs of the groups assigned to this iOS Protection Policy. | - |
| ExcludedGroups | Write | StringArray\[\] | List of IDs of the groups that are excluded from this iOS Protection Policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementApps.Read.All |
| Update | Group.Read.All, DeviceManagementApps.ReadWrite.All |

## attackSurfaceReductionRulesPolicyWindows10ConfigManager resource type

### Description

This resource configures an Intune Endpoint Protection Attack Surface Reduction Rules policy for a Windows 10 Device for Configuration Manager. This policy setting enables setting the state \(Block/Audit/Off/Warn\) for each attack surface reduction \(ASR\) rule. Each ASR rule listed can be set to one of the following states \(Block/Audit/Off/Warn\). The ASR rule ID and state should be added under the Options for this setting. Each entry must be listed as a name value pair. The name defines a valid ASR rule ID, while the value contains the status ID indicating the status of the rule.

For more information about ASR rule ID and status ID, see [Enable Attack Surface Reduction](https://learn.microsoft.com/en-us/windows/threat-protection/windows-defender-exploit-guard/enable-attack-surface-reduction).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Write | String | Identity of the endpoint protection attack surface protection rules policy for Windows 10. | - |
| DisplayName | Key | String | Display name of the endpoint protection attack surface protection rules policy for Windows 10. | - |
| Description | Write | String | Description of the endpoint protection attack surface protection rules policy for Windows 10. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the endpoint protection attack surface protection rules policy for Windows 10. | - |
| AttackSurfaceReductionOnlyExclusions | Write | StringArray\[\] | Exclude files and paths from attack surface reduction rules | - |
| BlockAbuseOfExploitedVulnerableSignedDrivers | Write | String | This rule prevents an application from writing a vulnerable signed driver to disk. | `off`, `block`, `audit`, `warn` |
| BlockAdobeReaderFromCreatingChildProcesses | Write | String | This rule prevents attacks by blocking Adobe Reader from creating processes. | `off`, `block`, `audit`, `warn` |
| BlockAllOfficeApplicationsFromCreatingChildProcesses | Write | String | This rule blocks Office apps from creating child processes. Office apps include Word, Excel, PowerPoint, OneNote, and Access. | `off`, `block`, `audit`, `warn` |
| BlockCredentialStealingFromWindowsLocalSecurityAuthoritySubsystem | Write | String | This rule helps prevent credential stealing by locking down Local Security Authority Subsystem Service \(LSASS\). | `off`, `block`, `audit`, `warn` |
| BlockExecutableContentFromEmailClientAndWebmail | Write | String | This rule blocks the following file types from launching from email opened within the Microsoft Outlook application, or Outlook.com and other popular webmail providers. | `off`, `block`, `audit`, `warn` |
| BlockExecutableFilesRunningUnlessTheyMeetPrevalenceAgeTrustedListCriterion | Write | String | This rule blocks executable files that don't meet a prevalence, age, or trusted list criteria, such as .exe, .dll, or .scr, from launching. | `off`, `block`, `audit`, `warn` |
| BlockExecutionOfPotentiallyObfuscatedScripts | Write | String | This rule detects suspicious properties within an obfuscated script. | `off`, `block`, `audit`, `warn` |
| BlockJavaScriptOrVBScriptFromLaunchingDownloadedExecutableContent | Write | String | This rule prevents scripts from launching potentially malicious downloaded content. | `off`, `block`, `audit`, `warn` |
| BlockOfficeApplicationsFromCreatingExecutableContent | Write | String | This rule prevents Office apps, including Word, Excel, and PowerPoint, from creating potentially malicious executable content, by blocking malicious code from being written to disk. | `off`, `block`, `audit`, `warn` |
| BlockOfficeApplicationsFromInjectingCodeIntoOtherProcesses | Write | String | This rule blocks code injection attempts from Office apps into other processes. | `off`, `block`, `audit`, `warn` |
| BlockOfficeCommunicationAppFromCreatingChildProcesses | Write | String | This rule prevents Outlook from creating child processes, while still allowing legitimate Outlook functions. | `off`, `block`, `audit`, `warn` |
| BlockPersistenceThroughWMIEventSubscription | Write | String | This rule prevents malware from abusing WMI to attain persistence on a device. | `off`, `block`, `audit`, `warn` |
| BlockProcessCreationsFromPSExecAndWMICommands | Write | String | This rule blocks processes created through PsExec and WMI from running. | `off`, `block`, `audit`, `warn` |
| BlockUntrustedUnsignedProcessesThatRunFromUSB | Write | String | With this rule, admins can prevent unsigned or untrusted executable files from running from USB removable drives, including SD cards. | `off`, `block`, `audit`, `warn` |
| BlockWin32APICallsFromOfficeMacros | Write | String | This rule prevents VBA macros from calling Win32 APIs. | `off`, `block`, `audit`, `warn` |
| UseAdvancedProtectionAgainstRansomware | Write | String | This rule provides an extra layer of protection against ransomware. | `off`, `block`, `audit`, `warn` |
| ControlledFolderAccessProtectedFolders | Write | StringArray\[\] | List of additional folders that need to be protected | - |
| ControlledFolderAccessAllowedApplications | Write | StringArray\[\] | List of apps that have access to protected folders. | - |
| EnableControlledFolderAccess | Write | String | This rule enable Controlled folder access which protects your data by checking apps against a list of known, trusted apps.values 0:disable, 1:enable, 2:audit, 3: Block disk modification only, 4: Audit disk modification only | `0`, `1`, `2`, `3`, `4` |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceAndAppManagementAssignmentFilter resource type

### Description

This resource represents the properties of the [Intune Assignment Filter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | DisplayName of the Assignment Filter. | - |
| Identity | Write | String | Key of the Assignment Filter. | - |
| Description | Write | String | Description of the Assignment Filter. | - |
| Platform | Write | String | Platform type of the devices on which the Assignment Filter will be applicable. | `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidAOSP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue` |
| Rule | Write | String | Rule definition of the Assignment Filter. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed | `Present`, `Absent` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | DeviceManagementConfiguration.Read.All |
| Update | DeviceManagementConfiguration.ReadWrite.All |

## deviceCategory resource type

### Description

This resource configures the Intune device categories.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the device category. | - |
| Description | Write | String | Description of the device category. | - |
| Ensure | Write | String | Present ensures the category exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | DeviceManagementManagedDevices.Read.All |
| Update | DeviceManagementManagedDevices.ReadWrite.All |

## deviceCleanupRule resource type

### Description

This resource configures the Intune device cleanup rule.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes'. | `Yes` |
| Enabled | Key | Boolean | Indicates whether the cleanup rule is enabled. | - |
| DeviceInactivityBeforeRetirementInDays | Write | UInt32 | Number of days until Intune devices are deleted. Minimum: 30, Maximum: 270. | - |
| Ensure | Write | String | Present ensures the category exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | DeviceManagementManagedDevices.Read.All |
| Update | DeviceManagementManagedDevices.ReadWrite.All |

## deviceCompliancePolicyAndroid resource type

### Description

This resource configures the settings of Android device compliance policies in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the Android device compliance policy. | - |
| Description | Write | String | Description of the Android device compliance policy. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the Intune Policy. | - |
| PasswordRequired | Write | Boolean | PasswordRequired of the Android device compliance policy. | - |
| PasswordMinimumLength | Write | UInt32 | PasswordMinimumLength of the Android device compliance policy. | - |
| PasswordRequiredType | Write | String | PasswordRequiredType of the Android device compliance policy. | `deviceDefault`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `numeric`, `numericComplex`, `any` |
| RequiredPasswordComplexity | Write | String | RequiredPasswordComplexity of the Android device compliance policy. | `none`, `low`, `medium`, `high` |
| PasswordMinutesOfInactivityBeforeLock | Write | UInt32 | PasswordMinutesOfInactivityBeforeLock of the Android device compliance policy. | - |
| PasswordExpirationDays | Write | UInt32 | PasswordExpirationDays of the Android device compliance policy. | - |
| PasswordPreviousPasswordBlockCount | Write | UInt32 | PasswordPreviousPasswordBlockCount of the Android device compliance policy. | - |
| PasswordSignInFailureCountBeforeFactoryReset | Write | UInt32 | PasswordSignInFailureCountBeforeFactoryReset of the Android device compliance policy. | - |
| SecurityPreventInstallAppsFromUnknownSources | Write | Boolean | SecurityPreventInstallAppsFromUnknownSources of the Android device compliance policy. | - |
| SecurityDisableUsbDebugging | Write | Boolean | SecurityDisableUsbDebugging of the Android device compliance policy. | - |
| SecurityRequireVerifyApps | Write | Boolean | SecurityRequireVerifyApps of the Android device compliance policy. | - |
| DeviceThreatProtectionEnabled | Write | Boolean | DeviceThreatProtectionEnabled of the Android device compliance policy. | - |
| DeviceThreatProtectionRequiredSecurityLevel | Write | String | DeviceThreatProtectionRequiredSecurityLevel of the Android device compliance policy. | `unavailable`, `secured`, `low`, `medium`, `high`, `notSet` |
| AdvancedThreatProtectionRequiredSecurityLevel | Write | String | AdvancedThreatProtectionRequiredSecurityLevel of the Android device compliance policy. | `unavailable`, `secured`, `low`, `medium`, `high`, `notSet` |
| SecurityBlockJailbrokenDevices | Write | Boolean | SecurityBlockJailbrokenDevices of the Android device compliance policy. | - |
| SecurityBlockDeviceAdministratorManagedDevices | Write | Boolean | SecurityBlockDeviceAdministratorManagedDevices of the Android device compliance policy. | - |
| OsMinimumVersion | Write | String | OsMinimumVersion of the Android device compliance policy. | - |
| OsMaximumVersion | Write | String | OsMaximumVersion of the Android device compliance policy. | - |
| MinAndroidSecurityPatchLevel | Write | String | MinAndroidSecurityPatchLevel of the Android device compliance policy. | - |
| StorageRequireEncryption | Write | Boolean | StorageRequireEncryption of the Android device compliance policy. | - |
| SecurityRequireSafetyNetAttestationBasicIntegrity | Write | Boolean | SecurityRequireSafetyNetAttestationBasicIntegrity of the Android device compliance policy. | - |
| SecurityRequireSafetyNetAttestationCertifiedDevice | Write | Boolean | SecurityRequireSafetyNetAttestationCertifiedDevice of the Android device compliance policy. | - |
| SecurityRequireGooglePlayServices | Write | Boolean | SecurityRequireGooglePlayServices of the Android device compliance policy. | - |
| SecurityRequireUpToDateSecurityProviders | Write | Boolean | SecurityRequireUpToDateSecurityProviders of the Android device compliance policy. | - |
| SecurityRequireCompanyPortalAppIntegrity | Write | Boolean | SecurityRequireCompanyPortalAppIntegrity of the Android device compliance policy. | - |
| ConditionStatementId | Write | String | ConditionStatementId of the Android device compliance policy. | - |
| RestrictedApps | Write | String | RestrictedApps of the Android device compliance policy. | - |
| RoleScopeTagIds | Write | String | RoleScopeTagIds of the Android device compliance policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Parameters

#### Microsoft Defender for Endpoint

- **Require the device to be at or under the machine risk score** Select the maximum allowed machine risk score for devices evaluated by Microsoft Defender for Endpoint. Devices that exceed this score get marked as noncompliant.

  - Not configured \(*default*\)
  - Clear
  - Low
  - Medium
  - High

#### Device Health

- **Devices managed with device administrator** Device administrator capabilities are superseded by Android Enterprise.

  - Not configured \(*default*\)
  - Block - Blocking device administrator will guide users to move to Android Enterprise Personally-Owned and Corporate-Owned Work Profile management to regain access.

#### Rooted devices

- **Prevent rooted devices from having corporate access. \(This compliance check is supported for Android 4.0 and above.\)**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Block - Mark rooted \(jailbroken\) devices as not compliant.

- **Require the device to be at or under the Device Threat Level** Use this setting to take the risk assessment from a connected Mobile Threat Defense service as a condition for compliance.

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Secured - This option is the most secure, as the device can't have any threats. If the device is detected with any level of threats, it's evaluated as noncompliant.
  - Low - The device is evaluated as compliant if only low-level threats are present. Anything higher puts the device in a noncompliant status.
  - Medium - The device is evaluated as compliant if existing threats on the device are low or medium level. If the device is detected to have high-level threats, it's determined to be noncompliant.
  - High - This option is the least secure, and allows all threat levels. It may be useful if you're using this solution only for reporting purposes.

#### Google Play Protect

- **Google Play Services is configured** Google Play services allows security updates, and is a base-level dependency for many security features on certified-Google devices.

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Require that the Google Play services app is installed and enabled.

- **Up-to-date security provider**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Require that an up-to-date security provider can protect a device from known vulnerabilities.

- **Threat scan on apps**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Require that the Android Verify Apps feature is enabled.

- **SafetyNet device attestation** Enter the level of SafetyNet attestation that must be met. Your options:

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Check basic integrity
  - Check basic integrity & certified devices

#### Device Properties

- **Operating System Version**

  - Minimum OS version When a device doesn't meet the minimum OS version requirement, it's reported as noncompliant. A link with information about how to upgrade is shown. The end user can choose to upgrade their device, and then get access to company resources.


  *By default, no version is configured.*


  - Maximum OS version When a device is using an OS version later than the version specified in the rule, access to company resources is blocked. The user is asked to contact their IT admin. Until a rule is changed to allow the OS version, this device can't access company resources.


  *By default, no version is configured.*

#### System Security

- **Encryption** Encryption of data storage on a device Supported on Android 4.0 and later, or KNOX 4.0 and later.

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Encrypt data storage on your devices. Devices are encrypted when you choose the Require a password to unlock mobile devices setting.

- **Device Security** Block apps from unknown sources Supported on Android 4.0 to Android 7.x. Not supported by Android 8.0 and later

  - Not configured \(*default*\) - this setting isn't evaluated for compliance or non-compliance.
  - Block - Block devices with Security > Unknown Sources enabled sources \(*supported on Android 4.0 through Android 7.x. Not supported on Android 8.0 and later.*\).


  To side-load apps, unknown sources must be allowed. If you're not side-loading Android apps, then set this feature to Block to enable this compliance policy.

- **Company portal app runtime integrity**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Choose Require to confirm the Company Portal app meets all the following requirements:

    - Has the default runtime environment installed
    - Is properly signed
    - Isn't in debug-mode

- **Block USB debugging on device** *\(Supported on Android 4.2 or later\)*

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Block - Prevent devices from using the USB debugging feature.

- **Minimum security patch level** *\(Supported on Android 6.0 or later\)*

  Select the oldest security patch level a device can have. Devices that aren't at least at this patch level are noncompliant. The date must be entered in the YYYY-MM-DD format.

  *By default, no date is configured.*
- **Restricted apps** Enter the App name and App bundle ID for apps that should be restricted, and then select Add. A device with at least one restricted app installed is marked as non-compliant.

#### Password

The available settings for passwords vary by the version of Android on the device.

##### All Android devices

The following settings are supported on Android 4.0 or later, and Knox 4.0 and later.

- **Maximum minutes of inactivity before password is required** This setting specifies the length of time without user input after which the mobile device screen is locked. Options range from 1 Minute to 8 Hours. The recommended value is 15 Minutes.

  - Not configured \(*default*\)

##### Android 10 and later

The following settings are supported on Android 10 or later, but not on Knox.

- **Password complexity** *This setting is supported on Android 10 or later, but not on Samsung Knox. On devices that run Android 9 and earlier or Samsung Knox, settings for the password length and type override this setting for complexity.*

  Specify the required password complexity.

  - None \(*default*\) - No password required.
  - Low - The password satisfies one of the following conditions:

    - Pattern
    - Numeric PIN has a repeating \(4444\) or ordered \(1234, 4321, 2468\) sequence.

  - Medium - The password satisfies one of the following conditions:

    - Numeric PIN doesn’t have a repeating \(4444\) or ordered \(1234, 4321, 2468\) sequence, and has minimum length of 4.
    - Alphabetic, with a minimum length of 4.
    - Alphanumeric, with a minimum length of 4.

  - High - The password satisfies one of the following conditions:

    - Numeric PIN doesn’t have a repeating \(4444\) or ordered \(1234, 4321, 2468\) sequence, and has minimum length of 8.
    - Alphabetic, with a minimum length of 6.
    - Alphanumeric, with a minimum length of 6.

##### Android 9 and earlier or Samsung Knox

*The following settings are supported on Android 9.0 and earlier, and any version of Samsung Knox.*

- **Require a password to unlock mobile devices** This setting specifies whether to require users to enter a password before access is granted to information on their mobile devices. Recommended value: Require

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Users must enter a password before they can access their device.

When set to Require, the following setting can be configured:

- **Required password type** Choose if a password should include only numeric characters, or a mix of numerals and other characters.

  - Device Default - To evaluate password compliance, be sure to select a password strength other than Device default.
  - Low security biometric
  - At least numeric
  - Numeric complex - Repeated or consecutive numerals, such as 1111 or 1234, aren't allowed.
  - At least alphabetic
  - At least alphanumeric
  - At least alphanumeric with symbols


  Based on the configuration of this setting, one or more of the following options are available:


  - Minimum password length Enter the minimum number of digits or characters that the user's password must have.
  - Maximum minutes of inactivity before password is required Enter the idle time before the user must reenter their password. When you choose Not configured \(*default*\), this setting isn't evaluated for compliance or non-compliance.
  - Number of days until password expires Select the number of days before the password expires and the user must create a new password.
  - Number of previous passwords to prevent reuse Enter the number of recent passwords that can't be reused. Use this setting to restrict the user from creating previously used passwords.

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | DeviceManagementConfiguration.ReadWrite.All |

## deviceCompliancePolicyAndroidDeviceOwner resource type

### Description

This resource configures the settings of Android Work Profile device compliance policies in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the Android Device Owner device compliance policy. | - |
| Description | Write | String | Description of the Android Device Owner device compliance policy. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the Intune Policy. | - |
| DeviceThreatProtectionEnabled | Write | Boolean | DeviceThreatProtectionEnabled of the Android Device Owner device compliance policy. | - |
| DeviceThreatProtectionRequiredSecurityLevel | Write | String | DeviceThreatProtectionRequiredSecurityLevel of the Android Device Owner device compliance policy. | - |
| AdvancedThreatProtectionRequiredSecurityLevel | Write | String | AdvancedThreatProtectionRequiredSecurityLevel of the Android Device Owner device compliance policy. | - |
| SecurityRequireSafetyNetAttestationBasicIntegrity | Write | Boolean | SecurityRequireSafetyNetAttestationBasicIntegrity of the Android Device Owner device compliance policy. | - |
| SecurityRequireSafetyNetAttestationCertifiedDevice | Write | Boolean | SecurityRequireSafetyNetAttestationCertifiedDevice of the Android Device Owner device compliance policy. | - |
| osMinimumVersion | Write | String | osMinimumVersion of the Android Device Owner device compliance policy. | - |
| osMaximumVersion | Write | String | osMaximumVersion of the Android Device Owner device compliance policy. | - |
| passwordRequired | Write | Boolean | PasswordRequired of the Android Device Owner device compliance policy. | - |
| passwordMinimumLength | Write | UInt32 | PasswordMinimumLength of the Android Device Owner device compliance policy. | - |
| PasswordRequiredType | Write | String | PasswordRequiredType of the Android Device Owner device compliance policy. | `deviceDefault`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `numeric`, `numericComplex`, `any` |
| PasswordMinutesOfInactivityBeforeLock | Write | UInt32 | PasswordMinutesOfInactivityBeforeLock of the Android Device Owner device compliance policy. | - |
| PasswordExpirationDays | Write | UInt32 | PasswordExpirationDays of the Android Device Owner device compliance policy. | - |
| PasswordPreviousPasswordCountToBlock | Write | UInt32 | PasswordPreviousPasswordCountToBlock of the Android Device Owner device compliance policy. | - |
| StorageRequireEncryption | Write | Boolean | StorageRequireEncryption of the Android Device Owner device compliance policy. | - |
| SecurityRequireIntuneAppIntegrity | Write | Boolean | SecurityRequireIntuneAppIntegrity of the Android Device Owner device compliance policy. | - |
| RoleScopeTagIds | Write | StringArray\[\] | List of Scope Tags for this Entity instance. Inherited from deviceConfiguration | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Parameters

#### Microsoft Defender for Endpoint - *for Personally-Owned Work Profile*

- **Require the device to be at or under the machine risk score** Select the maximum allowed machine risk score for devices evaluated by Microsoft Defender for Endpoint. Devices which exceed this score get marked as noncompliant.

  - Not configured \(*default*\)
  - Clear
  - Low
  - Medium
  - High

#### Device Health - *for Personally-Owned Work Profile*

- **Rooted devices**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Block - Mark rooted \(jailbroken\) devices as not compliant.

- **Require the device to be at or under the Device Threat Level** Select the maximum allowed device threat level evaluated by your mobile threat defense service. Devices that exceed this threat level are marked noncompliant. To use this setting, choose the allowed threat level:

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Secured - This option is the most secure, and means that the device can't have any threats. If the device is detected with any level of threats, it's evaluated as noncompliant.
  - Low - The device is evaluated as compliant if only low-level threats are present. Anything higher puts the device in a noncompliant status.
  - Medium - The device is evaluated as compliant if the threats that are present on the device are low or medium level. If the device is detected to have high-level threats, it's determined to be noncompliant.
  - High - This option is the least secure, as it allows all threat levels. It may be useful if you're using this solution only for reporting purposes.

#### Google Play Protect - *for Personally-Owned Work Profile*

- **Google Play Services is configured**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Require that the Google Play services app is installed and enabled. Google Play services allows security updates, and is a base-level dependency for many security features on certified-Google devices.

- **Up-to-date security provider**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Require that an up-to-date security provider can protect a device from known vulnerabilities.

- **SafetyNet device attestation** Enter the level of SafetyNet attestation that must be met. Your options:

  - Not configured \(*default*\) - Setting isn't evaluated for compliance or non-compliance.
  - Check basic integrity
  - Check basic integrity & certified devices

Note:

- On Android Enterprise devices, Threat scan on apps is a device configuration policy. Using a configuration policy, administrators can enable the setting on a device. See Android Enterprise device restriction settings.

#### Device Properties - *for Personally-Owned Work Profile*

- **Operating System Version - *for Personally-Owned Work Profile***

  - Minimum OS version When a device doesn't meet the minimum OS version requirement, it's reported as non-compliant. A link with information on how to upgrade is shown. The end user can upgrade their device, and then access organization resources.


  *By default, no version is configured.*

- **Maximum OS version** When a device is using an OS version later than the version in the rule, access to organization resources is blocked. The user is asked to contact their IT administrator. Until a rule is changed to allow the OS version, this device can't access organization resources.

  *By default, no version is configured.*

#### System security - for *Personally-Owned Work Profile*

- **Require a password to unlock mobile devices**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Users must enter a password before they can access their device.


  *This setting applies at the device level. If you only need to require a password at the Personally-Owned Work Profile level, then use a configuration policy. See Android Enterprise device configuration settings.*

- **Required password type** Choose if a password should include only numeric characters, or a mix of numerals and other characters. Your options:

  - Device Default
  - Low security biometric
  - At least numeric \(*default*\): Enter the minimum password length a user must enter, between 4 and 16 characters.
  - Numeric complex: Enter the minimum password length a user must enter, between 4 and 16 characters.
  - At least alphabetic: Enter the minimum password length a user must enter, between 4 and 16 characters.
  - At least alphanumeric: Enter the minimum password length a user must enter, between 4 and 16 characters.
  - At least alphanumeric with symbols: Enter the minimum password length a user must enter, between 4 and 16 characters.


  Depending on the password type you select, the following settings are available:


  - Maximum minutes of inactivity before password is required Enter the idle time before the user must reenter their password. Options include the default of Not configured, and from 1 Minute to 8 hours.
  - Number of days until password expires Enter the number of days, between 1-365, until the device password must be changed. For example, to change the password after 60 days, enter 60. When the password expires, users are prompted to create a new password.
  - Minimum password length Enter the minimum length the password must have, between 4 and 16 characters.
  - Number of previous passwords to prevent reuse Enter the number of recent passwords that can't be reused. Use this setting to restrict the user from creating previously used passwords.

#### Encryption - *for Personally-Owned Work Profile*

- **Encryption of data storage on device**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Encrypt data storage on your devices.


  You don't have to configure this setting because Android Enterprise devices enforce encryption.

#### Device Security - *for Personally-Owned Work Profile*

- **Block apps from unknown sources**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Block - Block devices with Security > Unknown Sources enabled sources \(supported on Android 4.0 through Android 7.x. Not supported by Android 8.0 and later\).


  *To side-load apps, unknown sources must be allowed. If you're not side-loading Android apps, then set this feature to Block to enable this compliance policy.*

- **Company portal app runtime integrity**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Choose Require to confirm the Company Portal app meets all the following requirements:

    - Has the default runtime environment installed
    - Is properly signed
    - Isn't in debug-mode
    - Is installed from a known source

- **Block USB debugging on device**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Block - Prevent devices from using the USB debugging feature.

*You don't have to configure this setting because USB debugging is already disabled on Android Enterprise devices.*

- **Minimum security patch level** Select the oldest security patch level a device can have. Devices that aren't at least at this patch level are noncompliant. The date must be entered in the YYYY-MM-DD format.

*By default, no date is configured.*

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceCompliancePolicyAndroidWorkProfile resource type

### Description

This resource configures the settings of Android Work Profile device compliance policies in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the AndroidWorkProfile device compliance policy. | - |
| Description | Write | String | Description of the AndroidWorkProfile device compliance policy. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the Intune Policy. | - |
| PasswordRequired | Write | Boolean | PasswordRequired of the AndroidWorkProfile device compliance policy. | - |
| PasswordMinimumLength | Write | UInt32 | PasswordMinimumLength of the AndroidWorkProfile device compliance policy. | - |
| PasswordRequiredType | Write | String | PasswordRequiredType of the AndroidWorkProfile device compliance policy. | `deviceDefault`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `numeric`, `numericComplex`, `any` |
| PasswordMinutesOfInactivityBeforeLock | Write | UInt32 | PasswordMinutesOfInactivityBeforeLock of the AndroidWorkProfile device compliance policy. | - |
| PasswordExpirationDays | Write | UInt32 | PasswordExpirationDays of the AndroidWorkProfile device compliance policy. | - |
| PasswordPreviousPasswordBlockCount | Write | UInt32 | PasswordPreviousPasswordBlockCount of the AndroidWorkProfile device compliance policy. | - |
| PasswordSignInFailureCountBeforeFactoryReset | Write | UInt32 | PasswordSignInFailureCountBeforeFactoryReset of the AndroidWorkProfile device compliance policy. | - |
| SecurityPreventInstallAppsFromUnknownSources | Write | Boolean | SecurityPreventInstallAppsFromUnknownSources of the AndroidWorkProfile device compliance policy. | - |
| SecurityDisableUsbDebugging | Write | Boolean | SecurityDisableUsbDebugging of the AndroidWorkProfile device compliance policy. | - |
| SecurityRequireVerifyApps | Write | Boolean | SecurityRequireVerifyApps of the AndroidWorkProfile device compliance policy. | - |
| DeviceThreatProtectionEnabled | Write | Boolean | DeviceThreatProtectionEnabled of the AndroidWorkProfile device compliance policy. | - |
| DeviceThreatProtectionRequiredSecurityLevel | Write | String | DeviceThreatProtectionRequiredSecurityLevel of the AndroidWorkProfile device compliance policy. | `unavailable`, `secured`, `low`, `medium`, `high`, `notSet` |
| AdvancedThreatProtectionRequiredSecurityLevel | Write | String | AdvancedThreatProtectionRequiredSecurityLevel of the AndroidWorkProfile device compliance policy. | `unavailable`, `secured`, `low`, `medium`, `high`, `notSet` |
| SecurityBlockJailbrokenDevices | Write | Boolean | SecurityBlockJailbrokenDevices of the AndroidWorkProfile device compliance policy. | - |
| OsMinimumVersion | Write | String | OsMinimumVersion of the AndroidWorkProfile device compliance policy. | - |
| OsMaximumVersion | Write | String | OsMaximumVersion of the AndroidWorkProfile device compliance policy. | - |
| MinAndroidSecurityPatchLevel | Write | String | MinAndroidSecurityPatchLevel of the AndroidWorkProfile device compliance policy. | - |
| StorageRequireEncryption | Write | Boolean | StorageRequireEncryption of the AndroidWorkProfile device compliance policy. | - |
| SecurityRequireSafetyNetAttestationBasicIntegrity | Write | Boolean | SecurityRequireSafetyNetAttestationBasicIntegrity of the AndroidWorkProfile device compliance policy. | - |
| SecurityRequireSafetyNetAttestationCertifiedDevice | Write | Boolean | SecurityRequireSafetyNetAttestationCertifiedDevice of the AndroidWorkProfile device compliance policy. | - |
| SecurityRequireGooglePlayServices | Write | Boolean | SecurityRequireGooglePlayServices of the AndroidWorkProfile device compliance policy. | - |
| SecurityRequireUpToDateSecurityProviders | Write | Boolean | SecurityRequireUpToDateSecurityProviders of the AndroidWorkProfile device compliance policy. | - |
| SecurityRequireCompanyPortalAppIntegrity | Write | Boolean | SecurityRequireCompanyPortalAppIntegrity of the AndroidWorkProfile device compliance policy. | - |
| SecurityRequiredAndroidSafetyNetEvaluationType | Write | String | Require a specific SafetyNet evaluation type for compliance. | `basic`, `hardwareBacked` |
| RoleScopeTagIds | Write | String | RoleScopeTagIds of the AndroidWorkProfile device compliance policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Parameters

#### Microsoft Defender for Endpoint - *for Personally-Owned Work Profile*

- **Require the device to be at or under the machine risk score** Select the maximum allowed machine risk score for devices evaluated by Microsoft Defender for Endpoint. Devices which exceed this score get marked as noncompliant.

  - Not configured \(*default*\)
  - Clear
  - Low
  - Medium
  - High

#### Device Health - *for Personally-Owned Work Profile*

- **Rooted devices**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Block - Mark rooted \(jailbroken\) devices as not compliant.

- **Require the device to be at or under the Device Threat Level** Select the maximum allowed device threat level evaluated by your mobile threat defense service. Devices that exceed this threat level are marked noncompliant. To use this setting, choose the allowed threat level:

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Secured - This option is the most secure, and means that the device can't have any threats. If the device is detected with any level of threats, it's evaluated as noncompliant.
  - Low - The device is evaluated as compliant if only low-level threats are present. Anything higher puts the device in a noncompliant status.
  - Medium - The device is evaluated as compliant if the threats that are present on the device are low or medium level. If the device is detected to have high-level threats, it's determined to be noncompliant.
  - High - This option is the least secure, as it allows all threat levels. It may be useful if you're using this solution only for reporting purposes.

#### Google Play Protect - *for Personally-Owned Work Profile*

- **Google Play Services is configured**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Require that the Google Play services app is installed and enabled. Google Play services allows security updates, and is a base-level dependency for many security features on certified-Google devices.

- **Up-to-date security provider**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Require that an up-to-date security provider can protect a device from known vulnerabilities.

- **SafetyNet device attestation** Enter the level of SafetyNet attestation that must be met. Your options:

  - Not configured \(*default*\) - Setting isn't evaluated for compliance or non-compliance.
  - Check basic integrity
  - Check basic integrity & certified devices


  Note:


  - On Android Enterprise devices, Threat scan on apps is a device configuration policy. Using a configuration policy, administrators can enable the setting on a device. See Android Enterprise device restriction settings.

#### Device Properties - *for Personally-Owned Work Profile*

- **Operating System Version - *for Personally-Owned Work Profile***

  - Minimum OS version When a device doesn't meet the minimum OS version requirement, it's reported as non-compliant. A link with information on how to upgrade is shown. The end user can upgrade their device, and then access organization resources.


  *By default, no version is configured.*

- **Maximum OS version** When a device is using an OS version later than the version in the rule, access to organization resources is blocked. The user is asked to contact their IT administrator. Until a rule is changed to allow the OS version, this device can't access organization resources.

  *By default, no version is configured.*

#### System security - for *Personally-Owned Work Profile*

- **Require a password to unlock mobile devices**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Users must enter a password before they can access their device.


  *This setting applies at the device level. If you only need to require a password at the Personally-Owned Work Profile level, then use a configuration policy. See Android Enterprise device configuration settings.*

- **Required password type** Choose if a password should include only numeric characters, or a mix of numerals and other characters. Your options:

  - Device Default
  - Low security biometric
  - At least numeric \(*default*\): Enter the minimum password length a user must enter, between 4 and 16 characters.
  - Numeric complex: Enter the minimum password length a user must enter, between 4 and 16 characters.
  - At least alphabetic: Enter the minimum password length a user must enter, between 4 and 16 characters.
  - At least alphanumeric: Enter the minimum password length a user must enter, between 4 and 16 characters.
  - At least alphanumeric with symbols: Enter the minimum password length a user must enter, between 4 and 16 characters.


  Depending on the password type you select, the following settings are available:


  - Maximum minutes of inactivity before password is required Enter the idle time before the user must reenter their password. Options include the default of Not configured, and from 1 Minute to 8 hours.
  - Number of days until password expires Enter the number of days, between 1-365, until the device password must be changed. For example, to change the password after 60 days, enter 60. When the password expires, users are prompted to create a new password.
  - Minimum password length Enter the minimum length the password must have, between 4 and 16 characters.
  - Number of previous passwords to prevent reuse Enter the number of recent passwords that can't be reused. Use this setting to restrict the user from creating previously used passwords.

#### Encryption - *for Personally-Owned Work Profile*

- **Encryption of data storage on device**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Encrypt data storage on your devices.


  You don't have to configure this setting because Android Enterprise devices enforce encryption.

#### Device Security - *for Personally-Owned Work Profile*

- **Block apps from unknown sources**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Block - Block devices with Security > Unknown Sources enabled sources \(supported on Android 4.0 through Android 7.x. Not supported by Android 8.0 and later\).


  *To side-load apps, unknown sources must be allowed. If you're not side-loading Android apps, then set this feature to Block to enable this compliance policy.*

- **Company portal app runtime integrity**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Require - Choose Require to confirm the Company Portal app meets all the following requirements:

    - Has the default runtime environment installed
    - Is properly signed
    - Isn't in debug-mode
    - Is installed from a known source

- **Block USB debugging on device**

  - Not configured \(*default*\) - This setting isn't evaluated for compliance or non-compliance.
  - Block - Prevent devices from using the USB debugging feature.

*You don't have to configure this setting because USB debugging is already disabled on Android Enterprise devices.*

- **Minimum security patch level** Select the oldest security patch level a device can have. Devices that aren't at least at this patch level are noncompliant. The date must be entered in the YYYY-MM-DD format.

*By default, no date is configured.*

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceCompliancePolicyiOS resource type

### Description

This resource configures the Intune compliance policies for iOs devices.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the iOS device compliance policy. | - |
| Description | Write | String | Description of the iOS device compliance policy. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the Intune Policy. | - |
| PasscodeBlockSimple | Write | Boolean | PasscodeBlockSimple of the iOS device compliance policy. | - |
| PasscodeExpirationDays | Write | UInt32 | PasscodeExpirationDays of the iOS device compliance policy. | - |
| PasscodeMinimumLength | Write | UInt32 | PasscodeMinimumLength of the iOS device compliance policy. | - |
| PasscodeMinutesOfInactivityBeforeLock | Write | UInt32 | PasscodeMinutesOfInactivityBeforeLock of the iOS device compliance policy. | - |
| PasscodeMinutesOfInactivityBeforeScreenTimeout | Write | UInt32 | Minutes of inactivity before the screen times out. | - |
| PasscodePreviousPasscodeBlockCount | Write | UInt32 | PasscodePreviousPasscodeBlockCount of the iOS device compliance policy. | - |
| PasscodeMinimumCharacterSetCount | Write | UInt32 | PasscodeMinimumCharacterSetCount of the iOS device compliance policy. | - |
| PasscodeRequiredType | Write | String | PasscodeRequiredType of the iOS device compliance policy. | `deviceDefault`, `alphanumeric`, `numeric` |
| PasscodeRequired | Write | Boolean | PasscodeRequired of the iOS device compliance policy. | - |
| OsMinimumVersion | Write | String | OsMinimumVersion of the iOS device compliance policy. | - |
| OsMaximumVersion | Write | String | OsMaximumVersion of the iOS device compliance policy. | - |
| OsMinimumBuildVersion | Write | String | Minimum IOS build version. | - |
| OsMaximumBuildVersion | Write | String | Maximum IOS build version. | - |
| SecurityBlockJailbrokenDevices | Write | Boolean | SecurityBlockJailbrokenDevices of the iOS device compliance policy. | - |
| DeviceThreatProtectionEnabled | Write | Boolean | DeviceThreatProtectionEnabled of the iOS device compliance policy. | - |
| DeviceThreatProtectionRequiredSecurityLevel | Write | String | Require Mobile Threat Protection minimum risk level to report noncompliance. | `unavailable`, `secured`, `low`, `medium`, `high`, `notSet` |
| AdvancedThreatProtectionRequiredSecurityLevel | Write | String | MDATP Require Mobile Threat Protection minimum risk level to report noncompliance. | `unavailable`, `secured`, `low`, `medium`, `high`, `notSet` |
| ManagedEmailProfileRequired | Write | Boolean | ManagedEmailProfileRequired of the iOS device compliance policy. | - |
| RestrictedApps | Write | MSFT\_appListItem\[\] | Credentials of the Intune Admin | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_appListItem

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| name | Write | String | The application name. | - |
| publisher | Write | String | The publisher of the application. | - |
| appStoreUrl | Write | String | The Store URL of the application. | - |
| appId | Write | String | The application or bundle identifier of the application. | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceCompliancePolicymacOS resource type

### Description

This resource configures the settings of MacOS compliance policies in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the MacOS device compliance policy. | - |
| Description | Write | String | Description of the MacOS device compliance policy. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the Intune Policy. | - |
| PasswordRequired | Write | Boolean | PasswordRequired of the MacOS device compliance policy. | - |
| PasswordBlockSimple | Write | Boolean | PasswordBlockSimple of the MacOS device compliance policy. | - |
| PasswordExpirationDays | Write | UInt32 | PasswordExpirationDays of the MacOS device compliance policy. | - |
| PasswordMinimumLength | Write | UInt32 | PasswordMinimumLength of the MacOS device compliance policy. | - |
| PasswordMinutesOfInactivityBeforeLock | Write | UInt32 | PasswordMinutesOfInactivityBeforeLock of the MacOS device compliance policy. | - |
| PasswordPreviousPasswordBlockCount | Write | UInt32 | PasswordPreviousPasswordBlockCount of the MacOS device compliance policy. | - |
| PasswordMinimumCharacterSetCount | Write | UInt32 | PasswordMinimumCharacterSetCount of the MacOS device compliance policy. | - |
| PasswordRequiredType | Write | String | PasswordRequiredType of the MacOS device compliance policy. | `DeviceDefault`, `Alphanumeric`, `Numeric` |
| OsMinimumVersion | Write | String | OsMinimumVersion of the MacOS device compliance policy. | - |
| OsMaximumVersion | Write | String | OsMaximumVersion of the MacOS device compliance policy. | - |
| OsMinimumBuildVersion | Write | String | Minimum MacOS build version. | - |
| OsMaximumBuildVersion | Write | String | Maximum MacOS build version. | - |
| SystemIntegrityProtectionEnabled | Write | Boolean | SystemIntegrityProtectionEnabled of the MacOS device compliance policy. | - |
| DeviceThreatProtectionEnabled | Write | Boolean | DeviceThreatProtectionEnabled of the MacOS device compliance policy. | - |
| DeviceThreatProtectionRequiredSecurityLevel | Write | String | DeviceThreatProtectionRequiredSecurityLevel of the MacOS device compliance policy. | `Unavailable`, `Secured`, `Low`, `Medium`, `High`, `NotSet` |
| AdvancedThreatProtectionRequiredSecurityLevel | Write | String | AdvancedThreatProtectionRequiredSecurityLevel of the MacOS device compliance policy. | `Unavailable`, `Secured`, `Low`, `Medium`, `High`, `NotSet` |
| StorageRequireEncryption | Write | Boolean | StorageRequireEncryption of the MacOS device compliance policy. | - |
| GatekeeperAllowedAppSource | Write | String | System and Privacy setting that determines which download locations apps can be run from on a macOS device. | `notConfigured`, `macAppStore`, `macAppStoreAndIdentifiedDevelopers`, `anywhere` |
| FirewallEnabled | Write | Boolean | FirewallEnabled of the MacOS device compliance policy. | - |
| FirewallBlockAllIncoming | Write | Boolean | FirewallBlockAllIncoming of the MacOS device compliance policy. | - |
| FirewallEnableStealthMode | Write | Boolean | FirewallEnableStealthMode of the MacOS device compliance policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Parameters

#### Device Health

- **Require a system integrity protection**

  - Not configured *\(default\)* - This setting isn't evaluated for compliance or non-compliance.
  - Require - Require macOS devices to have System Integrity Protection enabled.

#### Device Properties

- **Minimum OS required** When a device doesn't meet the minimum OS version requirement, it's reported as non-compliant. A link with information on how to upgrade is shown. The device user can choose to upgrade their device. After that, they can access organization resources.
- **Maximum OS version allowed** When a device uses an OS version later than the version in the rule, access to organization resources is blocked. The device user is asked to contact their IT administrator. The device can't access organization resources until a rule changes to allow the OS version.
- **Minimum OS build version** When Apple publishes security updates, the build number is typically updated, not the OS version. Use this feature to enter a minimum allowed build number on the device.
- **Maximum OS build version** When Apple publishes security updates, the build number is typically updated, not the OS version. Use this feature to enter a maximum allowed build number on the device.

### System security settings

#### Password

- **Require a password to unlock mobile devices**

  - Not configured *\(default\)*
  - Require Users must enter a password before they can access their device.

- **Simple passwords**

  - Not configured *\(default\)* - Users can create passwords simple like 1234 or 1111.
  - Block - Users can't create simple passwords, such as 1234 or 1111.

- **Minimum password length**

  - Enter the minimum number of digits or characters that the password must have.

- **Password type**

  - Choose if a password should have only Numeric characters, or if there should be a mix of numbers and other characters \(Alphanumeric\).

- **Number of non-alphanumeric characters in password**

  - Enter the minimum number of special characters, such as &, #, %, !, and so on, that must be in the password.


  Setting a higher number requires the user to create a password that is more complex.

- **Maximum minutes of inactivity before password is required**

  - Enter the idle time before the user must reenter their password.

- **Password expiration \(days\)**

  - Select the number of days before the password expires, and they must create a new one.

- **Number of previous passwords to prevent reuse**

  - Enter the number of previously used passwords that can't be used.

#### Encryption

- **Encryption of data storage on device**

  - Not configured \(*default*\)
  - Require - Use *Require* to encrypt data storage on your devices.

#### Device Security

Firewall protects devices from unauthorized network access. You can use Firewall to control connections on a per-application basis.

- **Firewall**

  - Not configured *\(default\)* - This setting leaves the firewall turned off, and network traffic is allowed \(not blocked\).
  - Enable - Use Enable to help protect devices from unauthorized access. Enabling this feature allows you to handle incoming internet connections, and use stealth mode.

- **Incoming connections**

  - Not configured *\(default\)* - Allows incoming connections and sharing services.
  - Block - Block all incoming network connections except the connections required for basic internet services, such as DHCP, Bonjour, and IPSec. This setting also blocks all sharing services, including screen sharing, remote access, iTunes music sharing, and more.

- **Stealth Mode**

  - Not configured *\(default\)* - This setting leaves stealth mode turned off.
  - Enable - Turn on stealth mode to prevent devices from responding to probing requests, which can be made my malicious users. When enabled, the device continues to answer incoming requests for authorized apps.

#### Gatekeeper

For more information, see Gatekeeper on macOS.

- **Allow apps downloaded from these locations** Allows supported applications to be installed on your devices from different locations. Your location options:

  - Not configured *\(default\)* - The gatekeeper option has no impact on compliance or non-compliance.
  - Mac App Store - Only install apps for the Mac app store. Apps can't be installed from third parties nor identified developers. If a user selects Gatekeeper to install apps outside the Mac App Store, then the device is considered not compliant.
  - Mac App Store and identified developers - Install apps for the Mac app store and from identified developers. macOS checks the identity of developers, and does some other checks to verify app integrity. If a user selects Gatekeeper to install apps outside these options, then the device is considered not compliant.
  - Anywhere - Apps can be installed from anywhere, and by any developer. This option is the least secure.

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceCompliancePolicyWindows10 resource type

### Description

This resource configures the settings of Windows 10 compliance policies in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the Windows 10 device compliance policy. | - |
| Description | Write | String | Description of the Windows 10 device compliance policy. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| PasswordRequired | Write | Boolean | PasswordRequired of the Windows 10 device compliance policy. | - |
| PasswordBlockSimple | Write | Boolean | PasswordBlockSimple of the Windows 10 device compliance policy. | - |
| PasswordRequiredToUnlockFromIdle | Write | Boolean | PasswordRequiredToUnlockFromIdle of the Windows 10 device compliance policy. | - |
| PasswordMinutesOfInactivityBeforeLock | Write | UInt32 | PasswordMinutesOfInactivityBeforeLock of the Windows 10 device compliance policy. | - |
| PasswordExpirationDays | Write | UInt32 | PasswordExpirationDays of the Windows 10 device compliance policy. | - |
| PasswordMinimumLength | Write | UInt32 | PasswordMinimumLength of the Windows 10 device compliance policy. | - |
| PasswordMinimumCharacterSetCount | Write | UInt32 | PasswordMinimumCharacterSetCount of the Windows 10 device compliance policy. | - |
| PasswordRequiredType | Write | String | PasswordRequiredType of the Windows 10 device compliance policy. | `DeviceDefault`, `Alphanumeric`, `Numeric` |
| PasswordPreviousPasswordBlockCount | Write | UInt32 | PasswordPreviousPasswordBlockCount of the Windows 10 device compliance policy. | - |
| RequireHealthyDeviceReport | Write | Boolean | RequireHealthyDeviceReport of the Windows 10 device compliance policy. | - |
| OsMinimumVersion | Write | String | OsMinimumVersion of the Windows 10 device compliance policy. | - |
| OsMaximumVersion | Write | String | OsMaximumVersion of the Windows 10 device compliance policy. | - |
| MobileOsMinimumVersion | Write | String | MobileOsMinimumVersion of the Windows 10 device compliance policy. | - |
| MobileOsMaximumVersion | Write | String | MobileOsMaximumVersion of the Windows 10 device compliance policy. | - |
| EarlyLaunchAntiMalwareDriverEnabled | Write | Boolean | EarlyLaunchAntiMalwareDriverEnabled of the Windows 10 device compliance policy. | - |
| BitLockerEnabled | Write | Boolean | BitLockerEnabled of the Windows 10 device compliance policy. | - |
| SecureBootEnabled | Write | Boolean | SecureBootEnabled of the Windows 10 device compliance policy. | - |
| CodeIntegrityEnabled | Write | Boolean | CodeIntegrityEnabled of the Windows 10 device compliance policy. | - |
| StorageRequireEncryption | Write | Boolean | StorageRequireEncryption of the Windows 10 device compliance policy. | - |
| ActiveFirewallRequired | Write | Boolean | ActiveFirewallRequired of the Windows 10 device compliance policy. | - |
| DefenderEnabled | Write | Boolean | DefenderEnabled of the Windows 10 device compliance policy. | - |
| DefenderVersion | Write | String | DefenderVersion of the Windows 10 device compliance policy. | - |
| SignatureOutOfDate | Write | Boolean | SignatureOutOfDate of the Windows 10 device compliance policy. | - |
| RTPEnabled | Write | Boolean | RTPEnabled of the Windows 10 device compliance policy. | - |
| AntivirusRequired | Write | Boolean | AntivirusRequired of the Windows 10 device compliance policy. | - |
| AntiSpywareRequired | Write | Boolean | AntiSpywareRequired of the Windows 10 device compliance policy. | - |
| DeviceThreatProtectionEnabled | Write | Boolean | DeviceThreatProtectionEnabled of the Windows 10 device compliance policy. | - |
| DeviceThreatProtectionRequiredSecurityLevel | Write | String | DeviceThreatProtectionRequiredSecurityLevel of the Windows 10 device compliance policy. | `Unavailable`, `Secured`, `Low`, `Medium`, `High`, `NotSet` |
| ConfigurationManagerComplianceRequired | Write | Boolean | ConfigurationManagerComplianceRequired of the Windows 10 device compliance policy. | - |
| TpmRequired | Write | Boolean | TpmRequired of the Windows 10 device compliance policy. | - |
| DeviceCompliancePolicyScript | Write | String | DeviceCompliancePolicyScript of the Windows 10 device compliance policy. | - |
| ValidOperatingSystemBuildRanges | Write | StringArray\[\] | ValidOperatingSystemBuildRanges of the Windows 10 device compliance policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Parameters

#### Device Health

##### Windows Health Attestation Service evaluation rules

- **Require BitLocker:** Windows BitLocker Drive Encryption encrypts all data stored on the Windows operating system volume. BitLocker uses the Trusted Platform Module \(TPM\) to help protect the Windows operating system and user data. It also helps confirm that a computer isn't tampered with, even if its left unattended, lost, or stolen. If the computer is equipped with a compatible TPM, BitLocker uses the TPM to lock the encryption keys that protect the data. As a result, the keys can't be accessed until the TPM verifies the state of the computer.

  - Not configured *\(default\)* - This setting isn't evaluated for compliance or non-compliance.
  - Require - The device can protect data that's stored on the drive from unauthorized access when the system is off, or hibernates.


  Device HealthAttestation CSP - BitLockerStatus

- **Require Secure Boot to be enabled on the device:**

  - Not configured *\(default\)* - This setting isn't evaluated for compliance or non-compliance.
  - Require - The system is forced to boot to a factory trusted state. The core components that are used to boot the machine must have correct cryptographic signatures that are trusted by the organization that manufactured the device. The UEFI firmware verifies the signature before it lets the machine start. If any files are tampered with, which breaks their signature, the system doesn't boot.

#### Device Properties

##### Operating System Version

To discover build versions for all Windows 10 Feature Updates and Cumulative Updates \(to be used in some of the fields below\), see Windows 10 release information. Be sure to include the 10.0. prefix before the build numbers, as the following examples illustrate.

- **Minimum OS version:** Enter the minimum allowed version in the major.minor.build.revision number format. To get the correct value, open a command prompt, and type ver. The ver command returns the version in the following format:

  Microsoft Windows \[Version 10.0.17134.1\]

  When a device has an earlier version than the OS version you enter, it's reported as noncompliant. A link with information on how to upgrade is shown. The end user can choose to upgrade their device. After they upgrade, they can access company resources.
- **Maximum OS version:** Enter the maximum allowed version, in the major.minor.build.revision number format. To get the correct value, open a command prompt, and type ver. The ver command returns the version in the following format:

  Microsoft Windows \[Version 10.0.17134.1\]

  When a device is using an OS version later than the version entered, access to organization resources is blocked. The end user is asked to contact their IT administrator. The device can't access organization resources until the rule is changed to allow the OS version.
- **Minimum OS required for mobile devices:** Enter the minimum allowed version, in the major.minor.build number format.

  When a device has an earlier version that the OS version you enter, it's reported as noncompliant. A link with information on how to upgrade is shown. The end user can choose to upgrade their device. After they upgrade, they can access company resources.
- **Maximum OS required for mobile devices:** Enter the maximum allowed version, in the major.minor.build number.

  When a device is using an OS version later than the version entered, access to organization resources is blocked. The end user is asked to contact their IT administrator. The device can't access organization resources until the rule is changed to allow the OS version.
- **Valid operating system builds:** Specify a list of minimum and maximum operating system builds. Valid operating system builds provides additional flexibility when compared against minimum and maximum OS versions. Consider a scenario where minimum OS version is set to 10.0.18362.xxx \(Windows 10 1903\) and maximum OS version is set to 10.0.18363.xxx \(Windows 10 1909\). This configuration can allow a Windows 10 1903 device that doesn't have recent cumulative updates installed to be identified as compliant. Minimum and maximum OS versions might be suitable if you have standardized on a single Windows 10 release, but might not address your requirements if you need to use multiple builds, each with specific patch levels. In such a case, consider leveraging valid operating system builds instead, which allows multiple builds to be specified as per the following example.

  Example: The following table is an example of a range for the acceptable operating systems versions for different Windows 10 releases. In this example, three different Feature Updates have been allowed \(1809, 1909 and 2004\). Specifically, only those versions of Windows and which have applied cumulative updates from June to September 2020 will be considered to be compliant. This is sample data only. The table includes a first column that includes any text you want to describe the entry, followed by the minimum and maximum OS version for that entry. The second and third columns must adhere to valid OS build versions in the major.minor.build.revision number format. After you define one or more entries, you can Export the list as a comma-separated values \(CSV\) file.

  | Description | Minimum OS version | Maximum OS version |
  | --- | --- | --- |
  | Win 10 2004 \(Jun-Sept 2020\) | 10.0.19041.329 | 10.0.19041.508 |
  | Win 10 1909 \(Jun-Sept 2020\) | 10.0.18363.900 | 10.0.18363.1110 |
  | Win 10 1809 \(Jun-Sept 2020\) | 10.0.17763.1282 | 10.0.17763.1490 |

#### Configuration Manager Compliance

Applies only to co-managed devices running Windows 10 and later. Intune-only devices return a not available status.

- **Require device compliance from Configuration Manager:**

  - Not configured *\(default\)* - Intune doesn't check for any of the Configuration Manager settings for compliance.
  - Require - Require all settings \(configuration items\) in Configuration Manager to be compliant.

#### System Security

##### Password

- **Require a password to unlock mobile devices:**

  - Not configured *\(default\)* - This setting isn't evaluated for compliance or non-compliance.
  - Require - Users must enter a password before they can access their device.

- **Simple passwords:**

  - Not configured *\(default\)* - Users can create simple passwords, such as 1234 or 1111.
  - Block - Users can't create simple passwords, such as 1234 or 1111.

- **Password type:** Choose the type of password or PIN required. Your options:

  - Device *\(default\)* - Require a password, numeric PIN, or alphanumeric PIN
  - Numeric - Require a password or numeric PIN
  - Alphanumeric - Require a password, or alphanumeric PIN. When set to Alphanumeric, the following settings are available:
  - Password complexity: Your options:

    - Require digits and lowercase letters *\(default\)*
    - Require digits, lowercase letters, and uppercase letters
    - Require digits, lowercase letters, uppercase letters, and special characters

- **Minimum password length:** Enter the minimum number of digits or characters that the password must have.
- **Maximum minutes of inactivity before password is required:** Enter the idle time before the user must reenter their password.
- **Password expiration \(days\):** Enter the number of days before the password expires, and they must create a new one, from 1-730.
- **Number of previous passwords to prevent reuse:** Enter the number of previously used passwords that can't be used.
- **Require password when device returns from idle state \(Mobile and Holographic\):**

  - Not configured *\(default\)*
  - Require - Require device users to enter the password every time the device returns from an idle state.


  **Important** When the password requirement is changed on a Windows desktop, users are impacted the next time they sign in, as that's when the device goes from idle to active. Users with passwords that meet the requirement are still prompted to change their passwords.

#### Encryption

- **Encryption of data storage on a device:** This setting applies to all drives on a device.

  - Not configured *\(default\)*
  - Require - Use Require to encrypt data storage on your devices.


  **Note** The Encryption of data storage on a device setting generically checks for the presence of encryption on the device, more specifically at the OS drive level. Currently, Intune supports only the encryption check with BitLocker. For a more robust encryption setting, consider using Require BitLocker, which leverages Windows Device Health Attestation to validate Bitlocker status at the TPM level.

#### Device Security

- **Firewall:**

  - Not configured *\(default\)* - Intune doesn't control the Microsoft Defender Firewall, nor change existing settings.
  - Require - Turn on the Microsoft Defender Firewall, and prevent users from turning it off.


  **Note** If the device immediately syncs after a reboot, or immediately syncs waking from sleep, then this setting may report as an Error. This scenario might not affect the overall device compliance status. To re-evaluate the compliance status, manually sync the device.

- **Trusted Platform Module \(TPM\):**

  - Not configured *\(default\)* - Intune doesn't check the device for a TPM chip version.
  - Require - Intune checks the TPM chip version for compliance. The device is compliant if the TPM chip version is greater than 0 \(zero\). The device isn't compliant if there'sn't a TPM version on the device.

- **Antivirus:**

  - Not configured *\(default\)* - Intune doesn't check for any antivirus solutions installed on the device.
  - Require - Check compliance using antivirus solutions that are registered with Windows Security Center, such as Symantec and Microsoft Defender.

- **Antispyware:**

  - Not configured *\(default\)* - Intune doesn't check for any antispyware solutions installed on the device.
  - Require - Check compliance using antispyware solutions that are registered with Windows Security Center, such as Symantec and Microsoft Defender.

#### Defender

The following compliance settings are supported with Windows 10 Desktop.

- **Microsoft Defender Antimalware:**

  - Not configured *\(default\)* - Intune doesn't control the service, nor change existing settings.
  - Require - Turn on the Microsoft Defender anti-malware service, and prevent users from turning it off.

- **Microsoft Defender Antimalware minimum version:** Enter the minimum allowed version of Microsoft Defender anti-malware service. For example, enter 4.11.0.0. When left blank, any version of the Microsoft Defender anti-malware service can be used.

  By *\(default\)*, no version is configured.
- **Microsoft Defender Antimalware security intelligence up-to-date:** Controls the Windows Security virus and threat protection updates on the devices.

  - Not configured *\(default\)* - Intune doesn't enforce any requirements.
  - Require - Force the Microsoft Defender security intelligence be up-to-date.

- **Real-time protection:**

  - Not configured \(*\(default\)*\) - Intune doesn't control this feature, nor change existing settings.
  - Require - Turn on real-time protection, which scans for malware, spyware, and other unwanted software.

#### Microsoft Defender for Endpoint

##### Microsoft Defender for Endpoint rules

For additional information on Microsoft Defender for Endpoint integration in conditional access scenarios, see Configure Conditional Access in Microsoft Defender for Endpoint.

- **Require the device to be at or under the machine risk score:** Use this setting to take the risk assessment from your defense threat services as a condition for compliance. Choose the maximum allowed threat level:

  - Not configured \(*\(default\)*\)
  - Clear -This option is the most secure, as the device can't have any threats. If the device is detected as having any level of threats, it's evaluated as non-compliant.
  - Low - The device is evaluated as compliant if only low-level threats are present. Anything higher puts the device in a non-compliant status.
  - Medium - The device is evaluated as compliant if existing threats on the device are low or medium level. If the device is detected to have high-level threats, it's determined to be non-compliant.
  - High - This option is the least secure, and allows all threat levels. It may be useful if you're using this solution only for reporting purposes.

#### Windows Holographic for Business

Windows Holographic for Business uses the Windows 10 and later platform. Windows Holographic for Business supports the following setting:

**System Security > Encryption > Encryption of data storage on device.** To verify device encryption on the Microsoft HoloLens, see Verify device encryption.

#### Surface Hub

Surface Hub uses the Windows 10 and later platform. Surface Hubs are supported for both compliance and Conditional Access. To enable these features on Surface Hubs, we recommend you enable Windows 10 automatic enrollment in Intune \(requires Azure Active Directory \(Microsoft Entra\)\), and target the Surface Hub devices as device groups. Surface Hubs are required to be Microsoft Entra joined for compliance and Conditional Access to work.

For guidance, see set up enrollment for Windows devices.

Special consideration for Surface Hubs running Windows 10 Team OS: Surface Hubs that run Windows 10 Team OS do not support the Microsoft Defender for Endpoint and Password compliance policies at this time. Therefore, for Surface Hubs that run Windows 10 Team OS set the following two settings to their *\(default\)* of *Not configured*:

- In the category Password, set Require a password to unlock mobile devices to the *\(default\)* of Not configured.
- In the category Microsoft Defender for Endpoint, set Require the device to be at or under the machine risk score to the *\(default\)* of Not configured.

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All, DeviceManagementScripts.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationAdministrativeTemplatePolicyWindows10 resource type

### Description

Intune Device Configuration Administrative Template Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Description | Write | String | User provided description for the resource object. | - |
| DisplayName | Key | String | User provided name for the resource object. | - |
| PolicyConfigurationIngestionType | Write | String | Type of definitions configured for this policy. Possible values are: unknown, custom, builtIn, mixed, unknownFutureValue. | `unknown`, `custom`, `builtIn`, `mixed`, `unknownFutureValue` |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| DefinitionValues | Write | GroupPolicyDefinitionValue\[\] | The list of enabled or disabled group policy definition values for the configuration. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### GroupPolicyDefinitionValueDefinition

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| CategoryPath | Write | String | The localized full category path for the policy. | - |
| ClassType | Write | String | Identifies the type of groups the policy can be applied to. Possible values are: user, machine. | `user`, `machine` |
| DisplayName | Write | String | The localized policy name. | - |
| ExplainText | Write | String | The localized explanation or help text associated with the policy. The default value is empty. | - |
| GroupPolicyCategoryId | Write | String | The category id of the parent category | - |
| HasRelatedDefinitions | Write | Boolean | Signifies whether or not there are related definitions to this definition | - |
| MinDeviceCspVersion | Write | String | Minimum required CSP version for device configuration in this definition | - |
| MinUserCspVersion | Write | String | Minimum required CSP version for user configuration in this definition | - |
| PolicyType | Write | String | Specifies the type of group policy. Possible values are: admxBacked, admxIngested. | `admxBacked`, `admxIngested` |
| SupportedOn | Write | String | Localized string used to specify what operating system or application version is affected by the policy. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |

#### GroupPolicyDefinitionValue

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ConfigurationType | Write | String | Specifies how the value should be configured. This can be either as a Policy or as a Preference. Possible values are: policy, preference. | `policy`, `preference` |
| Enabled | Write | Boolean | Enables or disables the associated group policy definition. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Definition | Write | GroupPolicyDefinitionValueDefinition | The associated group policy definition with the value. Read-Only. | - |
| PresentationValues | Write | GroupPolicyDefinitionValuePresentationValue\[\] | The associated group policy presentation values with the definition value. | - |

#### GroupPolicyDefinitionValuePresentationValue

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| BooleanValue | Write | Boolean | A value for the associated presentation. | - |
| DecimalValue | Write | UInt64 | A value for the associated presentation. | - |
| StringValue | Write | String | A value for the associated presentation. | - |
| KeyValuePairValues | Write | GroupPolicyDefinitionValuePresentationValueKeyValuePair\[\] | A list of pairs for the associated presentation. | - |
| StringValues | Write | StringArray\[\] | A list of pairs for the associated presentation. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| PresentationDefinitionId | Write | String | The unique identifier for presentation definition. Read-only. | - |
| PresentationDefinitionLabel | Write | String | The label of the presentation definition. Read-only. | - |
| odataType | Write | String | A value for the associated presentation. | `#microsoft.graph.groupPolicyPresentationValueBoolean`, `#microsoft.graph.groupPolicyPresentationValueDecimal`, `#microsoft.graph.groupPolicyPresentationValueList`, `#microsoft.graph.groupPolicyPresentationValueLongDecimal`, `#microsoft.graph.groupPolicyPresentationValueMultiText`, `#microsoft.graph.groupPolicyPresentationValueText` |

#### GroupPolicyDefinitionValuePresentationValueKeyValuePair

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Value | Write | String | Value for this key-value pair. | - |
| Name | Write | String | Name for this key-value pair. | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationCustomPolicyWindows10 resource type

### Description

Intune Device Configuration Custom Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| OmaSettings | Write | MSFT\_MicrosoftGraphomaSetting\[\] | OMA settings. This collection can contain a maximum of 1000 elements. | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| SupportsScopeTags | Write | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphOmaSetting

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Description | Write | String | Description. | - |
| DisplayName | Write | String | Display Name. | - |
| IsEncrypted | Write | Boolean | Indicates whether the value field is encrypted. This property is read-only. | - |
| OmaUri | Write | String | OMA. | - |
| SecretReferenceValueId | Write | String | ReferenceId for looking up secret for decryption. This property is read-only. | - |
| FileName | Write | String | File name associated with the Value property \(.cer\) | - |
| Value | Write | String | Value. \(Base64 encoded string\) | - |
| IsReadOnly | Write | Boolean | By setting to true, the CSP \(configuration service provider\) specified in the OMA-URI will perform a get, instead of set | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.omaSettingBase64`, `#microsoft.graph.omaSettingBoolean`, `#microsoft.graph.omaSettingDateTime`, `#microsoft.graph.omaSettingFloatingPoint`, `#microsoft.graph.omaSettingInteger`, `#microsoft.graph.omaSettingString`, `#microsoft.graph.omaSettingStringXml` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationDefenderForEndpointOnboardingPolicyWindows10 resource type

### Description

Intune Device Configuration Defender For Endpoint Onboarding Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AdvancedThreatProtectionAutoPopulateOnboardingBlob | Write | Boolean | Auto populate onboarding blob programmatically from Advanced Threat protection service | - |
| AdvancedThreatProtectionOffboardingBlob | Write | String | Windows Defender AdvancedThreatProtection Offboarding Blob. | - |
| AdvancedThreatProtectionOffboardingFilename | Write | String | Name of the file from which AdvancedThreatProtectionOffboardingBlob was obtained. | - |
| AdvancedThreatProtectionOnboardingBlob | Write | String | Windows Defender AdvancedThreatProtection Onboarding Blob. | - |
| AdvancedThreatProtectionOnboardingFilename | Write | String | Name of the file from which AdvancedThreatProtectionOnboardingBlob was obtained. | - |
| AllowSampleSharing | Write | Boolean | Windows Defender AdvancedThreatProtection 'Allow Sample Sharing' Rule | - |
| EnableExpeditedTelemetryReporting | Write | Boolean | Expedite Windows Defender Advanced Threat Protection telemetry reporting frequency. | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationDeliveryOptimizationPolicyWindows10 resource type

### Description

Intune Device Configuration Delivery Optimization Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| BackgroundDownloadFromHttpDelayInSeconds | Write | UInt64 | Specifies number of seconds to delay an HTTP source in a background download that is allowed to use peer-to-peer. Valid values 0 to 4294967295 | - |
| BandwidthMode | Write | MSFT\_MicrosoftGraphdeliveryOptimizationBandwidth | Specifies foreground and background bandwidth usage using percentages, absolutes, or hours. | - |
| CacheServerBackgroundDownloadFallbackToHttpDelayInSeconds | Write | UInt32 | Specifies number of seconds to delay a fall back from cache servers to an HTTP source for a background download. Valid values 0 to 2592000. | - |
| CacheServerForegroundDownloadFallbackToHttpDelayInSeconds | Write | UInt32 | Specifies number of seconds to delay a fall back from cache servers to an HTTP source for a foreground download. Valid values 0 to 2592000. | - |
| CacheServerHostNames | Write | StringArray\[\] | Specifies cache servers host names. | - |
| DeliveryOptimizationMode | Write | String | Specifies the download method that delivery optimization can use to manage network bandwidth consumption for large content distribution scenarios. Possible values are: userDefined, httpOnly, httpWithPeeringNat, httpWithPeeringPrivateGroup, httpWithInternetPeering, simpleDownload, bypassMode. | `userDefined`, `httpOnly`, `httpWithPeeringNat`, `httpWithPeeringPrivateGroup`, `httpWithInternetPeering`, `simpleDownload`, `bypassMode` |
| ForegroundDownloadFromHttpDelayInSeconds | Write | UInt64 | Specifies number of seconds to delay an HTTP source in a foreground download that is allowed to use peer-to-peer \(0-86400\). Valid values 0 to 86400 Specifying 0 sets Delivery Optimization to manage this setting using the cloud service. Valid values 0 to 86400 | - |
| GroupIdSource | Write | MSFT\_MicrosoftGraphdeliveryOptimizationGroupIdSource | Specifies to restrict peer selection to a specfic source. The options set in this policy only apply to Delivery Optimization mode Group \(2\) download mode. If Group \(2\) isn't set as Download mode, this policy will be ignored. For option 3 - DHCP Option ID, the client will query DHCP Option ID 234 and use the returned GUID value as the Group ID. | - |
| MaximumCacheAgeInDays | Write | UInt32 | Specifies the maximum time in days that each file is held in the Delivery Optimization cache after downloading successfully \(0-3650\). Valid values 0 to 3650 | - |
| MaximumCacheSize | Write | MSFT\_MicrosoftGraphdeliveryOptimizationMaxCacheSize | Specifies the maximum cache size that Delivery Optimization either as a percentage or in GB. | - |
| MinimumBatteryPercentageAllowedToUpload | Write | UInt32 | Specifies the minimum battery percentage to allow the device to upload data \(0-100\). Valid values 0 to 100 The default value is 0. The value 0 \(zero\) means 'not limited' and the cloud service default value will be used. Valid values 0 to 100 | - |
| MinimumDiskSizeAllowedToPeerInGigabytes | Write | UInt32 | Specifies the minimum disk size in GB to use Peer Caching \(1-100000\). Valid values 1 to 100000 Recommended values: 64 GB to 256 GB. Valid values 1 to 100000 | - |
| MinimumFileSizeToCacheInMegabytes | Write | UInt32 | Specifies the minimum content file size in MB enabled to use Peer Caching \(1-100000\). Valid values 1 to 100000 Recommended values: 1 MB to 100,000 MB. Valid values 1 to 100000 | - |
| MinimumRamAllowedToPeerInGigabytes | Write | UInt32 | Specifies the minimum RAM size in GB to use Peer Caching \(1-100000\). Valid values 1 to 100000 | - |
| ModifyCacheLocation | Write | String | Specifies the drive that Delivery Optimization should use for its cache. | - |
| RestrictPeerSelectionBy | Write | String | Specifies to restrict peer selection via selected option. | `notConfigured`, `subnetMask` |
| VpnPeerCaching | Write | String | Specifies whether the device is allowed to participate in Peer Caching while connected via VPN to the domain network. | `notConfigured`, `enabled`, `disabled` |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| SupportsScopeTags | Write | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphDeliveryOptimizationBandwidth

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| MaximumDownloadBandwidthInKilobytesPerSecond | Write | UInt64 | Specifies the maximum download bandwidth in KiloBytes/second that the device can use across all concurrent download activities using Delivery Optimization. Valid values 0 to 4294967295 | - |
| MaximumUploadBandwidthInKilobytesPerSecond | Write | UInt64 | Specifies the maximum upload bandwidth in KiloBytes/second that a device will use across all concurrent upload activity using Delivery Optimization \(0-4000000\). Valid values 0 to 4000000 The default value is 0, which permits unlimited possible bandwidth \(optimized for minimal usage of upload bandwidth\). Valid values 0 to 4000000 | - |
| BandwidthBackgroundPercentageHours | Write | MSFT\_MicrosoftGraphDeliveryOptimizationBandwidthBusinessHoursLimit | Background download percentage hours. | - |
| BandwidthForegroundPercentageHours | Write | MSFT\_MicrosoftGraphDeliveryOptimizationBandwidthBusinessHoursLimit | Foreground download percentage hours. | - |
| MaximumBackgroundBandwidthPercentage | Write | UInt32 | Specifies the maximum background download bandwidth that Delivery Optimization uses across all concurrent download activities as a percentage of available download bandwidth \(0-100\). Valid values 0 to 100 | - |
| MaximumForegroundBandwidthPercentage | Write | UInt32 | Specifies the maximum foreground download bandwidth that Delivery Optimization uses across all concurrent download activities as a percentage of available download bandwidth \(0-100\). Valid values 0 to 100 The default value 0 \(zero\) means that Delivery Optimization dynamically adjusts to use the available bandwidth for foreground downloads. Valid values 0 to 100 | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.deliveryOptimizationBandwidthAbsolute`, `#microsoft.graph.deliveryOptimizationBandwidthHoursWithPercentage`, `#microsoft.graph.deliveryOptimizationBandwidthPercentage` |

#### MSFT\_MicrosoftGraphDeliveryOptimizationBandwidthBusinessHoursLimit

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| BandwidthBeginBusinessHours | Write | UInt32 | Specifies the beginning of business hours using a 24-hour clock \(0-23\). Valid values 0 to 23 | - |
| BandwidthEndBusinessHours | Write | UInt32 | Specifies the end of business hours using a 24-hour clock \(0-23\). Valid values 0 to 23 | - |
| BandwidthPercentageDuringBusinessHours | Write | UInt32 | Specifies the percentage of bandwidth to limit during business hours \(0-100\). Valid values 0 to 100 | - |
| BandwidthPercentageOutsideBusinessHours | Write | UInt32 | Specifies the percentage of bandwidth to limit outsidse business hours \(0-100\). Valid values 0 to 100 | - |

#### MSFT\_MicrosoftGraphDeliveryOptimizationGroupIdSource

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| GroupIdCustom | Write | String | Specifies an arbitrary group ID that the device belongs to | - |
| GroupIdSourceOption | Write | String | Set this policy to restrict peer selection to a specific source. Possible values are: notConfigured, adSite, authenticatedDomainSid, dhcpUserOption, dnsSuffix. | `notConfigured`, `adSite`, `authenticatedDomainSid`, `dhcpUserOption`, `dnsSuffix` |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.deliveryOptimizationGroupIdCustom`, `#microsoft.graph.deliveryOptimizationGroupIdSourceOptions` |

#### MSFT\_MicrosoftGraphDeliveryOptimizationMaxCacheSize

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| MaximumCacheSizeInGigabytes | Write | UInt64 | Specifies the maximum size in GB of Delivery Optimization cache. Valid values 0 to 4294967295 | - |
| MaximumCacheSizePercentage | Write | UInt32 | Specifies the maximum cache size that Delivery Optimization can utilize, as a percentage of disk size \(1-100\). Valid values 1 to 100 | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.deliveryOptimizationMaxCacheSizeAbsolute`, `#microsoft.graph.deliveryOptimizationMaxCacheSizePercentage` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationDomainJoinPolicyWindows10 resource type

### Description

Intune Device Configuration Domain Join Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ActiveDirectoryDomainName | Write | String | Active Directory domain name to join. | - |
| ComputerNameStaticPrefix | Write | String | Fixed prefix to be used for computer name. | - |
| ComputerNameSuffixRandomCharCount | Write | UInt32 | Dynamically generated characters used as suffix for computer name. Valid values 3 to 14 | - |
| OrganizationalUnit | Write | String | Organizational unit \(OU\) where the computer account will be created. If this parameter is NULL, the well known computer object container will be used as published in the domain. | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| SupportsScopeTags | Write | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationEmailProfilePolicyWindows10 resource type

### Description

Intune Device Configuration Email Profile Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AccountName | Write | String | Account name. | - |
| DurationOfEmailToSync | Write | String | Duration of email to sync. Possible values are: userDefined, oneDay, threeDays, oneWeek, twoWeeks, oneMonth, unlimited. | `userDefined`, `oneDay`, `threeDays`, `oneWeek`, `twoWeeks`, `oneMonth`, `unlimited` |
| EmailAddressSource | Write | String | Email attribute that is picked from AAD and injected into this profile before installing on the device. Possible values are: userPrincipalName, primarySmtpAddress. | `userPrincipalName`, `primarySmtpAddress` |
| EmailSyncSchedule | Write | String | Email sync schedule. Possible values are: userDefined, asMessagesArrive, manual, fifteenMinutes, thirtyMinutes, sixtyMinutes, basedOnMyUsage. | `userDefined`, `asMessagesArrive`, `manual`, `fifteenMinutes`, `thirtyMinutes`, `sixtyMinutes`, `basedOnMyUsage` |
| HostName | Write | String | Exchange location that \(URL\) that the native mail app connects to. | - |
| RequireSsl | Write | Boolean | Indicates whether or not to use SSL. | - |
| SyncCalendar | Write | Boolean | Whether or not to sync the calendar. | - |
| SyncContacts | Write | Boolean | Whether or not to sync contacts. | - |
| SyncTasks | Write | Boolean | Whether or not to sync tasks. | - |
| CustomDomainName | Write | String | Custom domain name value used while generating an email profile before installing on the device. | - |
| UserDomainNameSource | Write | String | UserDomainname attribute that is picked from AAD and injected into this profile before installing on the device. Possible values are: fullDomainName, netBiosDomainName. | `fullDomainName`, `netBiosDomainName` |
| UsernameAADSource | Write | String | Name of the AAD field, that will be used to retrieve UserName for email profile. Possible values are: userPrincipalName, primarySmtpAddress, samAccountName. | `userPrincipalName`, `primarySmtpAddress`, `samAccountName` |
| UsernameSource | Write | String | Username attribute that is picked from AAD and injected into this profile before installing on the device. Possible values are: userPrincipalName, primarySmtpAddress. | `userPrincipalName`, `primarySmtpAddress` |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationEndpointProtectionPolicyWindows10 resource type

### Description

Intune Device Configuration Endpoint Protection Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ApplicationGuardAllowCameraMicrophoneRedirection | Write | Boolean | Gets or sets whether applications inside Microsoft Defender Application Guard can access the devices camera and microphone. | - |
| ApplicationGuardAllowFileSaveOnHost | Write | Boolean | Allow users to download files from Edge in the application guard container and save them on the host file system | - |
| ApplicationGuardAllowPersistence | Write | Boolean | Allow persisting user generated data inside the App Guard Containter \(favorites, cookies, web passwords, etc.\) | - |
| ApplicationGuardAllowPrintToLocalPrinters | Write | Boolean | Allow printing to Local Printers from Container | - |
| ApplicationGuardAllowPrintToNetworkPrinters | Write | Boolean | Allow printing to Network Printers from Container | - |
| ApplicationGuardAllowPrintToPDF | Write | Boolean | Allow printing to PDF from Container | - |
| ApplicationGuardAllowPrintToXPS | Write | Boolean | Allow printing to XPS from Container | - |
| ApplicationGuardAllowVirtualGPU | Write | Boolean | Allow application guard to use virtual GPU | - |
| ApplicationGuardBlockClipboardSharing | Write | String | Block clipboard to share data from Host to Container, or from Container to Host, or both ways, or neither ways. Possible values are: notConfigured, blockBoth, blockHostToContainer, blockContainerToHost, blockNone. | `notConfigured`, `blockBoth`, `blockHostToContainer`, `blockContainerToHost`, `blockNone` |
| ApplicationGuardBlockFileTransfer | Write | String | Block clipboard to transfer image file, text file or neither of them. Possible values are: notConfigured, blockImageAndTextFile, blockImageFile, blockNone, blockTextFile. | `notConfigured`, `blockImageAndTextFile`, `blockImageFile`, `blockNone`, `blockTextFile` |
| ApplicationGuardBlockNonEnterpriseContent | Write | Boolean | Block enterprise sites to load non-enterprise content, such as third party plug-ins | - |
| ApplicationGuardCertificateThumbprints | Write | StringArray\[\] | Allows certain device level Root Certificates to be shared with the Microsoft Defender Application Guard container. | - |
| ApplicationGuardEnabled | Write | Boolean | Enable Windows Defender Application Guard | - |
| ApplicationGuardEnabledOptions | Write | String | Enable Windows Defender Application Guard for newer Windows builds. Possible values are: notConfigured, enabledForEdge, enabledForOffice, enabledForEdgeAndOffice. | `notConfigured`, `enabledForEdge`, `enabledForOffice`, `enabledForEdgeAndOffice` |
| ApplicationGuardForceAuditing | Write | Boolean | Force auditing will persist Windows logs and events to meet security/compliance criteria \(sample events are user login-logoff, use of privilege rights, software installation, system changes, etc.\) | - |
| AppLockerApplicationControl | Write | String | Enables the Admin to choose what types of app to allow on devices. Possible values are: notConfigured, enforceComponentsAndStoreApps, auditComponentsAndStoreApps, enforceComponentsStoreAppsAndSmartlocker, auditComponentsStoreAppsAndSmartlocker. | `notConfigured`, `enforceComponentsAndStoreApps`, `auditComponentsAndStoreApps`, `enforceComponentsStoreAppsAndSmartlocker`, `auditComponentsStoreAppsAndSmartlocker` |
| BitLockerAllowStandardUserEncryption | Write | Boolean | Allows the admin to allow standard users to enable encrpytion during Microsoft Entra Join. | - |
| BitLockerDisableWarningForOtherDiskEncryption | Write | Boolean | Allows the Admin to disable the warning prompt for other disk encryption on the user machines. | - |
| BitLockerEnableStorageCardEncryptionOnMobile | Write | Boolean | Allows the admin to require encryption to be turned on using BitLocker. This policy is valid only for a mobile SKU. | - |
| BitLockerEncryptDevice | Write | Boolean | Allows the admin to require encryption to be turned on using BitLocker. | - |
| BitLockerFixedDrivePolicy | Write | MSFT\_MicrosoftGraphbitLockerFixedDrivePolicy | BitLocker Fixed Drive Policy. | - |
| BitLockerRecoveryPasswordRotation | Write | String | This setting initiates a client-driven recovery password rotation after an OS drive recovery \(either by using bootmgr or WinRE\). Possible values are: notConfigured, disabled, enabledForAzureAd, enabledForAzureAdAndHybrid. | `notConfigured`, `disabled`, `enabledForAzureAd`, `enabledForAzureAdAndHybrid` |
| BitLockerRemovableDrivePolicy | Write | MSFT\_MicrosoftGraphbitLockerRemovableDrivePolicy | BitLocker Removable Drive Policy. | - |
| BitLockerSystemDrivePolicy | Write | MSFT\_MicrosoftGraphbitLockerSystemDrivePolicy | BitLocker System Drive Policy. | - |
| DefenderAdditionalGuardedFolders | Write | StringArray\[\] | List of folder paths to be added to the list of protected folders | - |
| DefenderAdobeReaderLaunchChildProcess | Write | String | Value indicating the behavior of Adobe Reader from creating child processes. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderAdvancedRansomewareProtectionType | Write | String | Value indicating use of advanced protection against ransomeware. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderAllowBehaviorMonitoring | Write | Boolean | Allows or disallows Windows Defender Behavior Monitoring functionality. | - |
| DefenderAllowCloudProtection | Write | Boolean | To best protect your PC, Windows Defender will send information to Microsoft about any problems it finds. Microsoft will analyze that information, learn more about problems affecting you and other customers, and offer improved solutions. | - |
| DefenderAllowEndUserAccess | Write | Boolean | Allows or disallows user access to the Windows Defender UI. If disallowed, all Windows Defender notifications will also be suppressed. | - |
| DefenderAllowIntrusionPreventionSystem | Write | Boolean | Allows or disallows Windows Defender Intrusion Prevention functionality. | - |
| DefenderAllowOnAccessProtection | Write | Boolean | Allows or disallows Windows Defender On Access Protection functionality. | - |
| DefenderAllowRealTimeMonitoring | Write | Boolean | Allows or disallows Windows Defender Realtime Monitoring functionality. | - |
| DefenderAllowScanArchiveFiles | Write | Boolean | Allows or disallows scanning of archives. | - |
| DefenderAllowScanDownloads | Write | Boolean | Allows or disallows Windows Defender IOAVP Protection functionality. | - |
| DefenderAllowScanNetworkFiles | Write | Boolean | Allows or disallows a scanning of network files. | - |
| DefenderAllowScanRemovableDrivesDuringFullScan | Write | Boolean | Allows or disallows a full scan of removable drives. During a quick scan, removable drives may still be scanned. | - |
| DefenderAllowScanScriptsLoadedInInternetExplorer | Write | Boolean | Allows or disallows Windows Defender Script Scanning functionality. | - |
| DefenderAttackSurfaceReductionExcludedPaths | Write | StringArray\[\] | List of exe files and folders to be excluded from attack surface reduction rules | - |
| DefenderBlockEndUserAccess | Write | Boolean | Allows or disallows user access to the Windows Defender UI. If disallowed, all Windows Defender notifications will also be suppressed. | - |
| DefenderBlockPersistenceThroughWmiType | Write | String | Value indicating the behavior ofBlock persistence through WMI event subscription. Possible values are: userDefined, block, auditMode, warn, disable. | `userDefined`, `block`, `auditMode`, `warn`, `disable` |
| DefenderCheckForSignaturesBeforeRunningScan | Write | Boolean | This policy setting allows you to manage whether a check for new virus and spyware definitions will occur before running a scan. | - |
| DefenderCloudBlockLevel | Write | String | Added in Windows 10, version 1709. This policy setting determines how aggressive Windows Defender Antivirus will be in blocking and scanning suspicious files. Value type is integer. This feature requires the 'Join Microsoft MAPS' setting enabled in order to function. Possible values are: notConfigured, high, highPlus, zeroTolerance. | `notConfigured`, `high`, `highPlus`, `zeroTolerance` |
| DefenderCloudExtendedTimeoutInSeconds | Write | UInt32 | Added in Windows 10, version 1709. This feature allows Windows Defender Antivirus to block a suspicious file for up to 60 seconds, and scan it in the cloud to make sure it's safe. Value type is integer, range is 0 - 50. This feature depends on three other MAPS settings the must all be enabled- 'Configure the 'Block at First Sight' feature 'Join Microsoft MAPS' 'Send file samples when further analysis is required'. Valid values 0 to 50 | - |
| DefenderDaysBeforeDeletingQuarantinedMalware | Write | UInt32 | Time period \(in days\) that quarantine items will be stored on the system. Valid values 0 to 90 | - |
| DefenderDetectedMalwareActions | Write | MSFT\_MicrosoftGraphdefenderDetectedMalwareActions | Allows an administrator to specify any valid threat severity levels and the corresponding default action ID to take. | - |
| DefenderDisableBehaviorMonitoring | Write | Boolean | Allows or disallows Windows Defender Behavior Monitoring functionality. | - |
| DefenderDisableCatchupFullScan | Write | Boolean | This policy setting allows you to configure catch-up scans for scheduled full scans. A catch-up scan is a scan that is initiated because a regularly scheduled scan was missed. Usually these scheduled scans are missed because the computer was turned off at the scheduled time. | - |
| DefenderDisableCatchupQuickScan | Write | Boolean | This policy setting allows you to configure catch-up scans for scheduled quick scans. A catch-up scan is a scan that is initiated because a regularly scheduled scan was missed. Usually these scheduled scans are missed because the computer was turned off at the scheduled time. | - |
| DefenderDisableCloudProtection | Write | Boolean | To best protect your PC, Windows Defender will send information to Microsoft about any problems it finds. Microsoft will analyze that information, learn more about problems affecting you and other customers, and offer improved solutions. | - |
| DefenderDisableIntrusionPreventionSystem | Write | Boolean | Allows or disallows Windows Defender Intrusion Prevention functionality. | - |
| DefenderDisableOnAccessProtection | Write | Boolean | Allows or disallows Windows Defender On Access Protection functionality. | - |
| DefenderDisableRealTimeMonitoring | Write | Boolean | Allows or disallows Windows Defender Realtime Monitoring functionality. | - |
| DefenderDisableScanArchiveFiles | Write | Boolean | Allows or disallows scanning of archives. | - |
| DefenderDisableScanDownloads | Write | Boolean | Allows or disallows Windows Defender IOAVP Protection functionality. | - |
| DefenderDisableScanNetworkFiles | Write | Boolean | Allows or disallows a scanning of network files. | - |
| DefenderDisableScanRemovableDrivesDuringFullScan | Write | Boolean | Allows or disallows a full scan of removable drives. During a quick scan, removable drives may still be scanned. | - |
| DefenderDisableScanScriptsLoadedInInternetExplorer | Write | Boolean | Allows or disallows Windows Defender Script Scanning functionality. | - |
| DefenderEmailContentExecution | Write | String | Value indicating if execution of executable content \(exe, dll, ps, js, vbs, etc\) should be dropped from email \(webmail/mail-client\). Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderEmailContentExecutionType | Write | String | Value indicating if execution of executable content \(exe, dll, ps, js, vbs, etc\) should be dropped from email \(webmail/mail-client\). Possible values are: userDefined, block, auditMode, warn, disable. | `userDefined`, `block`, `auditMode`, `warn`, `disable` |
| DefenderEnableLowCpuPriority | Write | Boolean | This policy setting allows you to enable or disable low CPU priority for scheduled scans. | - |
| DefenderEnableScanIncomingMail | Write | Boolean | Allows or disallows scanning of email. | - |
| DefenderEnableScanMappedNetworkDrivesDuringFullScan | Write | Boolean | Allows or disallows a full scan of mapped network drives. | - |
| DefenderExploitProtectionXml | Write | String | Xml content containing information regarding exploit protection details. | - |
| DefenderExploitProtectionXmlFileName | Write | String | Name of the file from which DefenderExploitProtectionXml was obtained. | - |
| DefenderFileExtensionsToExclude | Write | StringArray\[\] | File extensions to exclude from scans and real time protection. | - |
| DefenderFilesAndFoldersToExclude | Write | StringArray\[\] | Files and folder to exclude from scans and real time protection. | - |
| DefenderGuardedFoldersAllowedAppPaths | Write | StringArray\[\] | List of paths to exe that are allowed to access protected folders | - |
| DefenderGuardMyFoldersType | Write | String | Value indicating the behavior of protected folders. Possible values are: userDefined, enable, auditMode, blockDiskModification, auditDiskModification. | `userDefined`, `enable`, `auditMode`, `blockDiskModification`, `auditDiskModification` |
| DefenderNetworkProtectionType | Write | String | Value indicating the behavior of NetworkProtection. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderOfficeAppsExecutableContentCreationOrLaunch | Write | String | Value indicating the behavior of Office applications/macros creating or launching executable content. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderOfficeAppsExecutableContentCreationOrLaunchType | Write | String | Value indicating the behavior of Office applications/macros creating or launching executable content. Possible values are: userDefined, block, auditMode, warn, disable. | `userDefined`, `block`, `auditMode`, `warn`, `disable` |
| DefenderOfficeAppsLaunchChildProcess | Write | String | Value indicating the behavior of Office application launching child processes. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderOfficeAppsLaunchChildProcessType | Write | String | Value indicating the behavior of Office application launching child processes. Possible values are: userDefined, block, auditMode, warn, disable. | `userDefined`, `block`, `auditMode`, `warn`, `disable` |
| DefenderOfficeAppsOtherProcessInjection | Write | String | Value indicating the behavior of Office applications injecting into other processes. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderOfficeAppsOtherProcessInjectionType | Write | String | Value indicating the behavior ofOffice applications injecting into other processes. Possible values are: userDefined, block, auditMode, warn, disable. | `userDefined`, `block`, `auditMode`, `warn`, `disable` |
| DefenderOfficeCommunicationAppsLaunchChildProcess | Write | String | Value indicating the behavior of Office communication applications, including Microsoft Outlook, from creating child processes. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderOfficeMacroCodeAllowWin32Imports | Write | String | Value indicating the behavior of Win32 imports from Macro code in Office. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderOfficeMacroCodeAllowWin32ImportsType | Write | String | Value indicating the behavior of Win32 imports from Macro code in Office. Possible values are: userDefined, block, auditMode, warn, disable. | `userDefined`, `block`, `auditMode`, `warn`, `disable` |
| DefenderPotentiallyUnwantedAppAction | Write | String | Added in Windows 10, version 1607. Specifies the level of detection for potentially unwanted applications \(PUAs\). Windows Defender alerts you when potentially unwanted software is being downloaded or attempts to install itself on your computer. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderPreventCredentialStealingType | Write | String | Value indicating if credential stealing from the Windows local security authority subsystem is permitted. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderProcessCreation | Write | String | Value indicating response to process creations originating from PSExec and WMI commands. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderProcessCreationType | Write | String | Value indicating response to process creations originating from PSExec and WMI commands. Possible values are: userDefined, block, auditMode, warn, disable. | `userDefined`, `block`, `auditMode`, `warn`, `disable` |
| DefenderProcessesToExclude | Write | StringArray\[\] | Processes to exclude from scans and real time protection. | - |
| DefenderScanDirection | Write | String | Controls which sets of files should be monitored. Possible values are: monitorAllFiles, monitorIncomingFilesOnly, monitorOutgoingFilesOnly. | `monitorAllFiles`, `monitorIncomingFilesOnly`, `monitorOutgoingFilesOnly` |
| DefenderScanMaxCpuPercentage | Write | UInt32 | Represents the average CPU load factor for the Windows Defender scan \(in percent\). The default value is 50. Valid values 0 to 100 | - |
| DefenderScanType | Write | String | Selects whether to perform a quick scan or full scan. Possible values are: userDefined, disabled, quick, full. | `userDefined`, `disabled`, `quick`, `full` |
| DefenderScheduledQuickScanTime | Write | String | Selects the time of day that the Windows Defender quick scan should run. For example, a value of 0=12:00AM, a value of 60=1:00AM, a value of 120=2:00, and so on, up to a value of 1380=11:00PM. The default value is 120 | - |
| DefenderScheduledScanDay | Write | String | Selects the day that the Windows Defender scan should run. Possible values are: userDefined, everyday, sunday, monday, tuesday, wednesday, thursday, friday, saturday, noScheduledScan. | `userDefined`, `everyday`, `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday`, `noScheduledScan` |
| DefenderScheduledScanTime | Write | String | Selects the time of day that the Windows Defender scan should run. | - |
| DefenderScriptDownloadedPayloadExecution | Write | String | Value indicating the behavior of js/vbs executing payload downloaded from Internet. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderScriptDownloadedPayloadExecutionType | Write | String | Value indicating the behavior of js/vbs executing payload downloaded from Internet. Possible values are: userDefined, block, auditMode, warn, disable. | `userDefined`, `block`, `auditMode`, `warn`, `disable` |
| DefenderScriptObfuscatedMacroCode | Write | String | Value indicating the behavior of obfuscated js/vbs/ps/macro code. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderScriptObfuscatedMacroCodeType | Write | String | Value indicating the behavior of obfuscated js/vbs/ps/macro code. Possible values are: userDefined, block, auditMode, warn, disable. | `userDefined`, `block`, `auditMode`, `warn`, `disable` |
| DefenderSecurityCenterBlockExploitProtectionOverride | Write | Boolean | Indicates whether or not to block user from overriding Exploit Protection settings. | - |
| DefenderSecurityCenterDisableAccountUI | Write | Boolean | Used to disable the display of the account protection area. | - |
| DefenderSecurityCenterDisableAppBrowserUI | Write | Boolean | Used to disable the display of the app and browser protection area. | - |
| DefenderSecurityCenterDisableClearTpmUI | Write | Boolean | Used to disable the display of the Clear TPM button. | - |
| DefenderSecurityCenterDisableFamilyUI | Write | Boolean | Used to disable the display of the family options area. | - |
| DefenderSecurityCenterDisableHardwareUI | Write | Boolean | Used to disable the display of the hardware protection area. | - |
| DefenderSecurityCenterDisableHealthUI | Write | Boolean | Used to disable the display of the device performance and health area. | - |
| DefenderSecurityCenterDisableNetworkUI | Write | Boolean | Used to disable the display of the firewall and network protection area. | - |
| DefenderSecurityCenterDisableNotificationAreaUI | Write | Boolean | Used to disable the display of the notification area control. The user needs to either sign out and sign in or reboot the computer for this setting to take effect. | - |
| DefenderSecurityCenterDisableRansomwareUI | Write | Boolean | Used to disable the display of the ransomware protection area. | - |
| DefenderSecurityCenterDisableSecureBootUI | Write | Boolean | Used to disable the display of the secure boot area under Device security. | - |
| DefenderSecurityCenterDisableTroubleshootingUI | Write | Boolean | Used to disable the display of the security process troubleshooting under Device security. | - |
| DefenderSecurityCenterDisableVirusUI | Write | Boolean | Used to disable the display of the virus and threat protection area. | - |
| DefenderSecurityCenterDisableVulnerableTpmFirmwareUpdateUI | Write | Boolean | Used to disable the display of update TPM Firmware when a vulnerable firmware is detected. | - |
| DefenderSecurityCenterHelpEmail | Write | String | The email address that is displayed to users. | - |
| DefenderSecurityCenterHelpPhone | Write | String | The phone number or Skype ID that is displayed to users. | - |
| DefenderSecurityCenterHelpURL | Write | String | The help portal URL this is displayed to users. | - |
| DefenderSecurityCenterITContactDisplay | Write | String | Configure where to display IT contact information to end users. Possible values are: notConfigured, displayInAppAndInNotifications, displayOnlyInApp, displayOnlyInNotifications. | `notConfigured`, `displayInAppAndInNotifications`, `displayOnlyInApp`, `displayOnlyInNotifications` |
| DefenderSecurityCenterNotificationsFromApp | Write | String | Notifications to show from the displayed areas of app. Possible values are: notConfigured, blockNoncriticalNotifications, blockAllNotifications. | `notConfigured`, `blockNoncriticalNotifications`, `blockAllNotifications` |
| DefenderSecurityCenterOrganizationDisplayName | Write | String | The company name that is displayed to the users. | - |
| DefenderSignatureUpdateIntervalInHours | Write | UInt32 | Specifies the interval \(in hours\) that will be used to check for signatures, so instead of using the ScheduleDay and ScheduleTime the check for new signatures will be set according to the interval. Valid values 0 to 24 | - |
| DefenderSubmitSamplesConsentType | Write | String | Checks for the user consent level in Windows Defender to send data. Possible values are: sendSafeSamplesAutomatically, alwaysPrompt, neverSend, sendAllSamplesAutomatically. | `sendSafeSamplesAutomatically`, `alwaysPrompt`, `neverSend`, `sendAllSamplesAutomatically` |
| DefenderUntrustedExecutable | Write | String | Value indicating response to executables that don't meet a prevalence, age, or trusted list criteria. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderUntrustedExecutableType | Write | String | Value indicating response to executables that don't meet a prevalence, age, or trusted list criteria. Possible values are: userDefined, block, auditMode, warn, disable. | `userDefined`, `block`, `auditMode`, `warn`, `disable` |
| DefenderUntrustedUSBProcess | Write | String | Value indicating response to untrusted and unsigned processes that run from USB. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderUntrustedUSBProcessType | Write | String | Value indicating response to untrusted and unsigned processes that run from USB. Possible values are: userDefined, block, auditMode, warn, disable. | `userDefined`, `block`, `auditMode`, `warn`, `disable` |
| DeviceGuardEnableSecureBootWithDMA | Write | Boolean | This property will be deprecated in May 2019 and will be replaced with property DeviceGuardSecureBootWithDMA. Specifies whether Platform Security Level is enabled at next reboot. | - |
| DeviceGuardEnableVirtualizationBasedSecurity | Write | Boolean | Turns On Virtualization Based Security\(VBS\). | - |
| DeviceGuardLaunchSystemGuard | Write | String | Allows the IT admin to configure the launch of System Guard. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| DeviceGuardLocalSystemAuthorityCredentialGuardSettings | Write | String | Turn on Credential Guard when Platform Security Level with Secure Boot and Virtualization Based Security are both enabled. Possible values are: notConfigured, enableWithUEFILock, enableWithoutUEFILock, disable. | `notConfigured`, `enableWithUEFILock`, `enableWithoutUEFILock`, `disable` |
| DeviceGuardSecureBootWithDMA | Write | String | Specifies whether Platform Security Level is enabled at next reboot. Possible values are: notConfigured, withoutDMA, withDMA. | `notConfigured`, `withoutDMA`, `withDMA` |
| DmaGuardDeviceEnumerationPolicy | Write | String | This policy is intended to provide additional security against external DMA capable devices. It allows for more control over the enumeration of external DMA capable devices incompatible with DMA Remapping/device memory isolation and sandboxing. This policy only takes effect when Kernel DMA Protection is supported and enabled by the system firmware. Kernel DMA Protection is a platform feature that can't be controlled via policy or by end user. It has to be supported by the system at the time of manufacturing. To check if the system supports Kernel DMA Protection, please check the Kernel DMA Protection field in the Summary page of MSINFO32.exe. Possible values are: deviceDefault, blockAll, allowAll. | `deviceDefault`, `blockAll`, `allowAll` |
| FirewallBlockStatefulFTP | Write | Boolean | Blocks stateful FTP connections to the device | - |
| FirewallCertificateRevocationListCheckMethod | Write | String | Specify how the certificate revocation list is to be enforced. Possible values are: deviceDefault, none, attempt, require. | `deviceDefault`, `none`, `attempt`, `require` |
| FirewallIdleTimeoutForSecurityAssociationInSeconds | Write | UInt32 | Configures the idle timeout for security associations, in seconds, from 300 to 3600 inclusive. This is the period after which security associations will expire and be deleted. Valid values 300 to 3600 | - |
| FirewallIPSecExemptionsAllowDHCP | Write | Boolean | Configures IPSec exemptions to allow both IPv4 and IPv6 DHCP traffic | - |
| FirewallIPSecExemptionsAllowICMP | Write | Boolean | Configures IPSec exemptions to allow ICMP | - |
| FirewallIPSecExemptionsAllowNeighborDiscovery | Write | Boolean | Configures IPSec exemptions to allow neighbor discovery IPv6 ICMP type-codes | - |
| FirewallIPSecExemptionsAllowRouterDiscovery | Write | Boolean | Configures IPSec exemptions to allow router discovery IPv6 ICMP type-codes | - |
| FirewallIPSecExemptionsNone | Write | Boolean | Configures IPSec exemptions to no exemptions | - |
| FirewallMergeKeyingModuleSettings | Write | Boolean | If an authentication set is not fully supported by a keying module, direct the module to ignore only unsupported authentication suites rather than the entire set | - |
| FirewallPacketQueueingMethod | Write | String | Configures how packet queueing should be applied in the tunnel gateway scenario. Possible values are: deviceDefault, disabled, queueInbound, queueOutbound, queueBoth. | `deviceDefault`, `disabled`, `queueInbound`, `queueOutbound`, `queueBoth` |
| FirewallPreSharedKeyEncodingMethod | Write | String | Select the preshared key encoding to be used. Possible values are: deviceDefault, none, utF8. | `deviceDefault`, `none`, `utF8` |
| FirewallProfileDomain | Write | MSFT\_MicrosoftGraphwindowsFirewallNetworkProfile | Configures the firewall profile settings for domain networks | - |
| FirewallProfilePrivate | Write | MSFT\_MicrosoftGraphwindowsFirewallNetworkProfile | Configures the firewall profile settings for private networks | - |
| FirewallProfilePublic | Write | MSFT\_MicrosoftGraphwindowsFirewallNetworkProfile | Configures the firewall profile settings for public networks | - |
| FirewallRules | Write | MSFT\_MicrosoftGraphwindowsFirewallRule\[\] | Configures the firewall rule settings. This collection can contain a maximum of 150 elements. | - |
| LanManagerAuthenticationLevel | Write | String | This security setting determines which challenge/response authentication protocol is used for network logons. Possible values are: lmAndNltm, lmNtlmAndNtlmV2, lmAndNtlmOnly, lmAndNtlmV2, lmNtlmV2AndNotLm, lmNtlmV2AndNotLmOrNtm. | `lmAndNltm`, `lmNtlmAndNtlmV2`, `lmAndNtlmOnly`, `lmAndNtlmV2`, `lmNtlmV2AndNotLm`, `lmNtlmV2AndNotLmOrNtm` |
| LanManagerWorkstationDisableInsecureGuestLogons | Write | Boolean | If enabled,the SMB client will allow insecure guest logons. If not configured, the SMB client will reject insecure guest logons. | - |
| LocalSecurityOptionsAdministratorAccountName | Write | String | Define a different account name to be associated with the security identifier \(SID\) for the account 'Administrator'. | - |
| LocalSecurityOptionsAdministratorElevationPromptBehavior | Write | String | Define the behavior of the elevation prompt for admins in Admin Approval Mode. Possible values are: notConfigured, elevateWithoutPrompting, promptForCredentialsOnTheSecureDesktop, promptForConsentOnTheSecureDesktop, promptForCredentials, promptForConsent, promptForConsentForNonWindowsBinaries. | `notConfigured`, `elevateWithoutPrompting`, `promptForCredentialsOnTheSecureDesktop`, `promptForConsentOnTheSecureDesktop`, `promptForCredentials`, `promptForConsent`, `promptForConsentForNonWindowsBinaries` |
| LocalSecurityOptionsAllowAnonymousEnumerationOfSAMAccountsAndShares | Write | Boolean | This security setting determines whether to allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. | - |
| LocalSecurityOptionsAllowPKU2UAuthenticationRequests | Write | Boolean | Block PKU2U authentication requests to this device to use online identities. | - |
| LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManager | Write | String | Edit the default Security Descriptor Definition Language string to allow or deny users and groups to make remote calls to the SAM. | - |
| LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManagerHelperBool | Write | Boolean | UI helper boolean for LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManager entity | - |
| LocalSecurityOptionsAllowSystemToBeShutDownWithoutHavingToLogOn | Write | Boolean | This security setting determines whether a computer can be shut down without having to log on to Windows. | - |
| LocalSecurityOptionsAllowUIAccessApplicationElevation | Write | Boolean | Allow UIAccess apps to prompt for elevation without using the secure desktop. | - |
| LocalSecurityOptionsAllowUIAccessApplicationsForSecureLocations | Write | Boolean | Allow UIAccess apps to prompt for elevation without using the secure desktop.Default is enabled | - |
| LocalSecurityOptionsAllowUndockWithoutHavingToLogon | Write | Boolean | Prevent a portable computer from being undocked without having to log in. | - |
| LocalSecurityOptionsBlockMicrosoftAccounts | Write | Boolean | Prevent users from adding new Microsoft accounts to this computer. | - |
| LocalSecurityOptionsBlockRemoteLogonWithBlankPassword | Write | Boolean | Enable Local accounts that are not password protected to log on from locations other than the physical device.Default is enabled | - |
| LocalSecurityOptionsBlockRemoteOpticalDriveAccess | Write | Boolean | Enabling this settings allows only interactively logged on user to access CD-ROM media. | - |
| LocalSecurityOptionsBlockUsersInstallingPrinterDrivers | Write | Boolean | Restrict installing printer drivers as part of connecting to a shared printer to admins only. | - |
| LocalSecurityOptionsClearVirtualMemoryPageFile | Write | Boolean | This security setting determines whether the virtual memory pagefile is cleared when the system is shut down. | - |
| LocalSecurityOptionsClientDigitallySignCommunicationsAlways | Write | Boolean | This security setting determines whether packet signing is required by the SMB client component. | - |
| LocalSecurityOptionsClientSendUnencryptedPasswordToThirdPartySMBServers | Write | Boolean | If this security setting is enabled, the Server Message Block \(SMB\) redirector is allowed to send plaintext passwords to non-Microsoft SMB servers that do not support password encryption during authentication. | - |
| LocalSecurityOptionsDetectApplicationInstallationsAndPromptForElevation | Write | Boolean | App installations requiring elevated privileges will prompt for admin credentials.Default is enabled | - |
| LocalSecurityOptionsDisableAdministratorAccount | Write | Boolean | Determines whether the Local Administrator account is enabled or disabled. | - |
| LocalSecurityOptionsDisableClientDigitallySignCommunicationsIfServerAgrees | Write | Boolean | This security setting determines whether the SMB client attempts to negotiate SMB packet signing. | - |
| LocalSecurityOptionsDisableGuestAccount | Write | Boolean | Determines if the Guest account is enabled or disabled. | - |
| LocalSecurityOptionsDisableServerDigitallySignCommunicationsAlways | Write | Boolean | This security setting determines whether packet signing is required by the SMB server component. | - |
| LocalSecurityOptionsDisableServerDigitallySignCommunicationsIfClientAgrees | Write | Boolean | This security setting determines whether the SMB server will negotiate SMB packet signing with clients that request it. | - |
| LocalSecurityOptionsDoNotAllowAnonymousEnumerationOfSAMAccounts | Write | Boolean | This security setting determines what additional permissions will be granted for anonymous connections to the computer. | - |
| LocalSecurityOptionsDoNotRequireCtrlAltDel | Write | Boolean | Require CTRL+ALT+DEL to be pressed before a user can log on. | - |
| LocalSecurityOptionsDoNotStoreLANManagerHashValueOnNextPasswordChange | Write | Boolean | This security setting determines if, at the next password change, the LAN Manager \(LM\) hash value for the new password is stored. Its not stored by default. | - |
| LocalSecurityOptionsFormatAndEjectOfRemovableMediaAllowedUser | Write | String | Define who is allowed to format and eject removable NTFS media. Possible values are: notConfigured, administrators, administratorsAndPowerUsers, administratorsAndInteractiveUsers. | `notConfigured`, `administrators`, `administratorsAndPowerUsers`, `administratorsAndInteractiveUsers` |
| LocalSecurityOptionsGuestAccountName | Write | String | Define a different account name to be associated with the security identifier \(SID\) for the account 'Guest'. | - |
| LocalSecurityOptionsHideLastSignedInUser | Write | Boolean | Do not display the username of the last person who signed in on this device. | - |
| LocalSecurityOptionsHideUsernameAtSignIn | Write | Boolean | Do not display the username of the person signing in to this device after credentials are entered and before the devices desktop is shown. | - |
| LocalSecurityOptionsInformationDisplayedOnLockScreen | Write | String | Configure the user information that is displayed when the session is locked. If not configured, user display name, domain and username are shown. Possible values are: notConfigured, administrators, administratorsAndPowerUsers, administratorsAndInteractiveUsers. | `notConfigured`, `administrators`, `administratorsAndPowerUsers`, `administratorsAndInteractiveUsers` |
| LocalSecurityOptionsInformationShownOnLockScreen | Write | String | Configure the user information that is displayed when the session is locked. If not configured, user display name, domain and username are shown. Possible values are: notConfigured, userDisplayNameDomainUser, userDisplayNameOnly, doNotDisplayUser. | `notConfigured`, `userDisplayNameDomainUser`, `userDisplayNameOnly`, `doNotDisplayUser` |
| LocalSecurityOptionsLogOnMessageText | Write | String | Set message text for users attempting to log in. | - |
| LocalSecurityOptionsLogOnMessageTitle | Write | String | Set message title for users attempting to log in. | - |
| LocalSecurityOptionsMachineInactivityLimit | Write | UInt32 | Define maximum minutes of inactivity on the interactive desktops login screen until the screen saver runs. Valid values 0 to 9999 | - |
| LocalSecurityOptionsMachineInactivityLimitInMinutes | Write | UInt32 | Define maximum minutes of inactivity on the interactive desktops login screen until the screen saver runs. Valid values 0 to 9999 | - |
| LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedClients | Write | String | This security setting allows a client to require the negotiation of 128-bit encryption and/or NTLMv2 session security. Possible values are: none, requireNtmlV2SessionSecurity, require128BitEncryption, ntlmV2And128BitEncryption. | `none`, `requireNtmlV2SessionSecurity`, `require128BitEncryption`, `ntlmV2And128BitEncryption` |
| LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedServers | Write | String | This security setting allows a server to require the negotiation of 128-bit encryption and/or NTLMv2 session security. Possible values are: none, requireNtmlV2SessionSecurity, require128BitEncryption, ntlmV2And128BitEncryption. | `none`, `requireNtmlV2SessionSecurity`, `require128BitEncryption`, `ntlmV2And128BitEncryption` |
| LocalSecurityOptionsOnlyElevateSignedExecutables | Write | Boolean | Enforce PKI certification path validation for a given executable file before it's permitted to run. | - |
| LocalSecurityOptionsRestrictAnonymousAccessToNamedPipesAndShares | Write | Boolean | By default, this security setting restricts anonymous access to shares and pipes to the settings for named pipes that can be accessed anonymously and Shares that can be accessed anonymously | - |
| LocalSecurityOptionsSmartCardRemovalBehavior | Write | String | This security setting determines what happens when the smart card for a logged-on user is removed from the smart card reader. Possible values are: noAction, lockWorkstation, forceLogoff, disconnectRemoteDesktopSession. | `noAction`, `lockWorkstation`, `forceLogoff`, `disconnectRemoteDesktopSession` |
| LocalSecurityOptionsStandardUserElevationPromptBehavior | Write | String | Define the behavior of the elevation prompt for standard users. Possible values are: notConfigured, automaticallyDenyElevationRequests, promptForCredentialsOnTheSecureDesktop, promptForCredentials. | `notConfigured`, `automaticallyDenyElevationRequests`, `promptForCredentialsOnTheSecureDesktop`, `promptForCredentials` |
| LocalSecurityOptionsSwitchToSecureDesktopWhenPromptingForElevation | Write | Boolean | Enable all elevation requests to go to the interactive user's desktop rather than the secure desktop. Prompt behavior policy settings for admins and standard users are used. | - |
| LocalSecurityOptionsUseAdminApprovalMode | Write | Boolean | Defines whether the built-in admin account uses Admin Approval Mode or runs all apps with full admin privileges.Default is enabled | - |
| LocalSecurityOptionsUseAdminApprovalModeForAdministrators | Write | Boolean | Define whether Admin Approval Mode and all UAC policy settings are enabled, default is enabled | - |
| LocalSecurityOptionsVirtualizeFileAndRegistryWriteFailuresToPerUserLocations | Write | Boolean | Virtualize file and registry write failures to per user locations | - |
| SmartScreenBlockOverrideForFiles | Write | Boolean | Allows IT Admins to control whether users can can ignore SmartScreen warnings and run malicious files. | - |
| SmartScreenEnableInShell | Write | Boolean | Allows IT Admins to configure SmartScreen for Windows. | - |
| UserRightsAccessCredentialManagerAsTrustedCaller | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right is used by Credential Manager during Backup/Restore. Users' saved credentials might be compromised if this privilege is given to other entities. Only states NotConfigured and Allowed are supported | - |
| UserRightsActAsPartOfTheOperatingSystem | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right allows a process to impersonate any user without authentication. The process can therefore gain access to the same local resources as that user. Only states NotConfigured and Allowed are supported | - |
| UserRightsAllowAccessFromNetwork | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users and groups are allowed to connect to the computer over the network. State Allowed is supported. | - |
| UserRightsBackupData | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users can bypass file, directory, registry, and other persistent objects permissions when backing up files and directories. Only states NotConfigured and Allowed are supported | - |
| UserRightsBlockAccessFromNetwork | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users and groups are block from connecting to the computer over the network. State Block is supported. | - |
| UserRightsChangeSystemTime | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users and groups can change the time and date on the internal clock of the computer. Only states NotConfigured and Allowed are supported | - |
| UserRightsCreateGlobalObjects | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This security setting determines whether users can create global objects that are available to all sessions. Users who can create global objects could affect processes that run under other users' sessions, which could lead to application failure or data corruption. Only states NotConfigured and Allowed are supported | - |
| UserRightsCreatePageFile | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users and groups can call an internal API to create and change the size of a page file. Only states NotConfigured and Allowed are supported | - |
| UserRightsCreatePermanentSharedObjects | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which accounts can be used by processes to create a directory object using the object manager. Only states NotConfigured and Allowed are supported | - |
| UserRightsCreateSymbolicLinks | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines if the user can create a symbolic link from the computer to which they are logged on. Only states NotConfigured and Allowed are supported | - |
| UserRightsCreateToken | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users/groups can be used by processes to create a token that can then be used to get access to any local resources when the process uses an internal API to create an access token. Only states NotConfigured and Allowed are supported | - |
| UserRightsDebugPrograms | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users can attach a debugger to any process or to the kernel. Only states NotConfigured and Allowed are supported | - |
| UserRightsDelegation | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users can set the Trusted for Delegation setting on a user or computer object. Only states NotConfigured and Allowed are supported. | - |
| UserRightsDenyLocalLogOn | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users can't log on to the computer. States NotConfigured, Blocked are supported | - |
| UserRightsGenerateSecurityAudits | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which accounts can be used by a process to add entries to the security log. The security log is used to trace unauthorized system access. Only states NotConfigured and Allowed are supported. | - |
| UserRightsImpersonateClient | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | Assigning this user right to a user allows programs running on behalf of that user to impersonate a client. Requiring this user right for this kind of impersonation prevents an unauthorized user from convincing a client to connect to a service that they have created and then impersonating that client, which can elevate the unauthorized user's permissions to administrative or system levels. Only states NotConfigured and Allowed are supported. | - |
| UserRightsIncreaseSchedulingPriority | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which accounts can use a process with Write Property access to another process to increase the execution priority assigned to the other process. Only states NotConfigured and Allowed are supported. | - |
| UserRightsLoadUnloadDrivers | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users can dynamically load and unload device drivers or other code in to kernel mode. Only states NotConfigured and Allowed are supported. | - |
| UserRightsLocalLogOn | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users can log on to the computer. States NotConfigured, Allowed are supported | - |
| UserRightsLockMemory | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which accounts can use a process to keep data in physical memory, which prevents the system from paging the data to virtual memory on disk. Only states NotConfigured and Allowed are supported. | - |
| UserRightsManageAuditingAndSecurityLogs | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users can specify object access auditing options for individual resources, such as files, Active Directory objects, and registry keys. Only states NotConfigured and Allowed are supported. | - |
| UserRightsManageVolumes | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users and groups can run maintenance tasks on a volume, such as remote defragmentation. Only states NotConfigured and Allowed are supported. | - |
| UserRightsModifyFirmwareEnvironment | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines who can modify firmware environment values. Only states NotConfigured and Allowed are supported. | - |
| UserRightsModifyObjectLabels | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which user accounts can modify the integrity label of objects, such as files, registry keys, or processes owned by other users. Only states NotConfigured and Allowed are supported. | - |
| UserRightsProfileSingleProcess | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users can use performance monitoring tools to monitor the performance of system processes. Only states NotConfigured and Allowed are supported. | - |
| UserRightsRemoteDesktopServicesLogOn | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users and groups are prohibited from logging on as a Remote Desktop Services client. Only states NotConfigured and Blocked are supported | - |
| UserRightsRemoteShutdown | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users are allowed to shut down a computer from a remote location on the network. Misuse of this user right can result in a denial of service. Only states NotConfigured and Allowed are supported. | - |
| UserRightsRestoreData | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users can bypass file, directory, registry, and other persistent objects permissions when restoring backed up files and directories, and determines which users can set any valid security principal as the owner of an object. Only states NotConfigured and Allowed are supported. | - |
| UserRightsTakeOwnership | Write | MSFT\_MicrosoftGraphdeviceManagementUserRightsSetting | This user right determines which users can take ownership of any securable object in the system, including Active Directory objects, files and folders, printers, registry keys, processes, and threads. Only states NotConfigured and Allowed are supported. | - |
| WindowsDefenderTamperProtection | Write | String | Configure windows defender TamperProtection settings. Possible values are: notConfigured, enable, disable. | `notConfigured`, `enable`, `disable` |
| XboxServicesAccessoryManagementServiceStartupMode | Write | String | This setting determines whether the Accessory management service's start type is Automatic\(2\), Manual\(3\), Disabled\(4\). Default: Manual. Possible values are: manual, automatic, disabled. | `manual`, `automatic`, `disabled` |
| XboxServicesEnableXboxGameSaveTask | Write | Boolean | This setting determines whether xbox game save is enabled \(1\) or disabled \(0\). | - |
| XboxServicesLiveAuthManagerServiceStartupMode | Write | String | This setting determines whether Live Auth Manager service's start type is Automatic\(2\), Manual\(3\), Disabled\(4\). Default: Manual. Possible values are: manual, automatic, disabled. | `manual`, `automatic`, `disabled` |
| XboxServicesLiveGameSaveServiceStartupMode | Write | String | This setting determines whether Live Game save service's start type is Automatic\(2\), Manual\(3\), Disabled\(4\). Default: Manual. Possible values are: manual, automatic, disabled. | `manual`, `automatic`, `disabled` |
| XboxServicesLiveNetworkingServiceStartupMode | Write | String | This setting determines whether Networking service's start type is Automatic\(2\), Manual\(3\), Disabled\(4\). Default: Manual. Possible values are: manual, automatic, disabled. | `manual`, `automatic`, `disabled` |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| SupportsScopeTags | Write | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphBitLockerFixedDrivePolicy

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| EncryptionMethod | Write | String | Select the encryption method for fixed drives. Possible values are: aesCbc128, aesCbc256, xtsAes128, xtsAes256. | `aesCbc128`, `aesCbc256`, `xtsAes128`, `xtsAes256` |
| RecoveryOptions | Write | MSFT\_MicrosoftGraphBitLockerRecoveryOptions | This policy setting allows you to control how BitLocker-protected fixed data drives are recovered in the absence of the required credentials. This policy setting is applied when you turn on BitLocker. | - |
| RequireEncryptionForWriteAccess | Write | Boolean | This policy setting determines whether BitLocker protection is required for fixed data drives to be writable on a computer. | - |

#### MSFT\_MicrosoftGraphBitLockerRecoveryOptions

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| BlockDataRecoveryAgent | Write | Boolean | Indicates whether to block certificate-based data recovery agent. | - |
| EnableBitLockerAfterRecoveryInformationToStore | Write | Boolean | Indicates whether or not to enable BitLocker until recovery information is stored in AD DS. | - |
| EnableRecoveryInformationSaveToStore | Write | Boolean | Indicates whether or not to allow BitLocker recovery information to store in AD DS. | - |
| HideRecoveryOptions | Write | Boolean | Indicates whether or not to allow showing recovery options in BitLocker Setup Wizard for fixed or system disk. | - |
| RecoveryInformationToStore | Write | String | Configure what pieces of BitLocker recovery information are stored to AD DS. Possible values are: passwordAndKey, passwordOnly. | `passwordAndKey`, `passwordOnly` |
| RecoveryKeyUsage | Write | String | Indicates whether users are allowed or required to generate a 256-bit recovery key for fixed or system disk. Possible values are: blocked, required, allowed, notConfigured. | `blocked`, `required`, `allowed`, `notConfigured` |
| RecoveryPasswordUsage | Write | String | Indicates whether users are allowed or required to generate a 48-digit recovery password for fixed or system disk. Possible values are: blocked, required, allowed, notConfigured. | `blocked`, `required`, `allowed`, `notConfigured` |

#### MSFT\_MicrosoftGraphBitLockerRemovableDrivePolicy

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| BlockCrossOrganizationWriteAccess | Write | Boolean | This policy setting determines whether BitLocker protection is required for removable data drives to be writable on a computer. | - |
| EncryptionMethod | Write | String | Select the encryption method for removable drives. Possible values are: aesCbc128, aesCbc256, xtsAes128, xtsAes256. | `aesCbc128`, `aesCbc256`, `xtsAes128`, `xtsAes256` |
| RequireEncryptionForWriteAccess | Write | Boolean | Indicates whether to block write access to devices configured in another organization. If requireEncryptionForWriteAccess is false, this value does not affect. | - |

#### MSFT\_MicrosoftGraphBitLockerSystemDrivePolicy

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| EncryptionMethod | Write | String | Select the encryption method for operating system drives. Possible values are: aesCbc128, aesCbc256, xtsAes128, xtsAes256. | `aesCbc128`, `aesCbc256`, `xtsAes128`, `xtsAes256` |
| MinimumPinLength | Write | UInt32 | Indicates the minimum length of startup pin. Valid values 4 to 20 | - |
| PrebootRecoveryEnableMessageAndUrl | Write | Boolean | Enable pre-boot recovery message and Url. If requireStartupAuthentication is false, this value does not affect. | - |
| PrebootRecoveryMessage | Write | String | Defines a custom recovery message. | - |
| PrebootRecoveryUrl | Write | String | Defines a custom recovery URL. | - |
| RecoveryOptions | Write | MSFT\_MicrosoftGraphBitLockerRecoveryOptions | Allows to recover BitLocker encrypted operating system drives in the absence of the required startup key information. This policy setting is applied when you turn on BitLocker. | - |
| StartupAuthenticationBlockWithoutTpmChip | Write | Boolean | Indicates whether to allow BitLocker without a compatible TPM \(requires a password or a startup key on a USB flash drive\). | - |
| StartupAuthenticationRequired | Write | Boolean | Require additional authentication at startup. | - |
| StartupAuthenticationTpmKeyUsage | Write | String | Indicates if TPM startup key is allowed/required/disallowed. Possible values are: blocked, required, allowed, notConfigured. | `blocked`, `required`, `allowed`, `notConfigured` |
| StartupAuthenticationTpmPinAndKeyUsage | Write | String | Indicates if TPM startup pin key and key are allowed/required/disallowed. Possible values are: blocked, required, allowed, notConfigured. | `blocked`, `required`, `allowed`, `notConfigured` |
| StartupAuthenticationTpmPinUsage | Write | String | Indicates if TPM startup pin is allowed/required/disallowed. Possible values are: blocked, required, allowed, notConfigured. | `blocked`, `required`, `allowed`, `notConfigured` |
| StartupAuthenticationTpmUsage | Write | String | Indicates if TPM startup is allowed/required/disallowed. Possible values are: blocked, required, allowed, notConfigured. | `blocked`, `required`, `allowed`, `notConfigured` |

#### MSFT\_MicrosoftGraphDefenderDetectedMalwareActions

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| HighSeverity | Write | String | Indicates a Defender action to take for high severity Malware threat detected. Possible values are: deviceDefault, clean, quarantine, remove, allow, userDefined, block. | `deviceDefault`, `clean`, `quarantine`, `remove`, `allow`, `userDefined`, `block` |
| LowSeverity | Write | String | Indicates a Defender action to take for low severity Malware threat detected. Possible values are: deviceDefault, clean, quarantine, remove, allow, userDefined, block. | `deviceDefault`, `clean`, `quarantine`, `remove`, `allow`, `userDefined`, `block` |
| ModerateSeverity | Write | String | Indicates a Defender action to take for moderate severity Malware threat detected. Possible values are: deviceDefault, clean, quarantine, remove, allow, userDefined, block. | `deviceDefault`, `clean`, `quarantine`, `remove`, `allow`, `userDefined`, `block` |
| SevereSeverity | Write | String | Indicates a Defender action to take for severe severity Malware threat detected. Possible values are: deviceDefault, clean, quarantine, remove, allow, userDefined, block. | `deviceDefault`, `clean`, `quarantine`, `remove`, `allow`, `userDefined`, `block` |

#### MSFT\_MicrosoftGraphWindowsFirewallNetworkProfile

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AuthorizedApplicationRulesFromGroupPolicyMerged | Write | Boolean | Configures the firewall to merge authorized application rules from group policy with those from local store instead of ignoring the local store rules. When AuthorizedApplicationRulesFromGroupPolicyNotMerged and AuthorizedApplicationRulesFromGroupPolicyMerged are both true, AuthorizedApplicationRulesFromGroupPolicyMerged takes priority. | - |
| AuthorizedApplicationRulesFromGroupPolicyNotMerged | Write | Boolean | Configures the firewall to prevent merging authorized application rules from group policy with those from local store instead of ignoring the local store rules. When AuthorizedApplicationRulesFromGroupPolicyNotMerged and AuthorizedApplicationRulesFromGroupPolicyMerged are both true, AuthorizedApplicationRulesFromGroupPolicyMerged takes priority. | - |
| ConnectionSecurityRulesFromGroupPolicyMerged | Write | Boolean | Configures the firewall to merge connection security rules from group policy with those from local store instead of ignoring the local store rules. When ConnectionSecurityRulesFromGroupPolicyNotMerged and ConnectionSecurityRulesFromGroupPolicyMerged are both true, ConnectionSecurityRulesFromGroupPolicyMerged takes priority. | - |
| ConnectionSecurityRulesFromGroupPolicyNotMerged | Write | Boolean | Configures the firewall to prevent merging connection security rules from group policy with those from local store instead of ignoring the local store rules. When ConnectionSecurityRulesFromGroupPolicyNotMerged and ConnectionSecurityRulesFromGroupPolicyMerged are both true, ConnectionSecurityRulesFromGroupPolicyMerged takes priority. | - |
| FirewallEnabled | Write | String | Configures the host device to allow or block the firewall and advanced security enforcement for the network profile. Possible values are: notConfigured, blocked, allowed. | `notConfigured`, `blocked`, `allowed` |
| GlobalPortRulesFromGroupPolicyMerged | Write | Boolean | Configures the firewall to merge global port rules from group policy with those from local store instead of ignoring the local store rules. When GlobalPortRulesFromGroupPolicyNotMerged and GlobalPortRulesFromGroupPolicyMerged are both true, GlobalPortRulesFromGroupPolicyMerged takes priority. | - |
| GlobalPortRulesFromGroupPolicyNotMerged | Write | Boolean | Configures the firewall to prevent merging global port rules from group policy with those from local store instead of ignoring the local store rules. When GlobalPortRulesFromGroupPolicyNotMerged and GlobalPortRulesFromGroupPolicyMerged are both true, GlobalPortRulesFromGroupPolicyMerged takes priority. | - |
| InboundConnectionsBlocked | Write | Boolean | Configures the firewall to block all incoming connections by default. When InboundConnectionsRequired and InboundConnectionsBlocked are both true, InboundConnectionsBlocked takes priority. | - |
| InboundConnectionsRequired | Write | Boolean | Configures the firewall to allow all incoming connections by default. When InboundConnectionsRequired and InboundConnectionsBlocked are both true, InboundConnectionsBlocked takes priority. | - |
| InboundNotificationsBlocked | Write | Boolean | Prevents the firewall from displaying notifications when an application is blocked from listening on a port. When InboundNotificationsRequired and InboundNotificationsBlocked are both true, InboundNotificationsBlocked takes priority. | - |
| InboundNotificationsRequired | Write | Boolean | Allows the firewall to display notifications when an application is blocked from listening on a port. When InboundNotificationsRequired and InboundNotificationsBlocked are both true, InboundNotificationsBlocked takes priority. | - |
| IncomingTrafficBlocked | Write | Boolean | Configures the firewall to block all incoming traffic regardless of other policy settings. When IncomingTrafficRequired and IncomingTrafficBlocked are both true, IncomingTrafficBlocked takes priority. | - |
| IncomingTrafficRequired | Write | Boolean | Configures the firewall to allow incoming traffic pursuant to other policy settings. When IncomingTrafficRequired and IncomingTrafficBlocked are both true, IncomingTrafficBlocked takes priority. | - |
| OutboundConnectionsBlocked | Write | Boolean | Configures the firewall to block all outgoing connections by default. When OutboundConnectionsRequired and OutboundConnectionsBlocked are both true, OutboundConnectionsBlocked takes priority. This setting will get applied to Windows releases version 1809 and above. | - |
| OutboundConnectionsRequired | Write | Boolean | Configures the firewall to allow all outgoing connections by default. When OutboundConnectionsRequired and OutboundConnectionsBlocked are both true, OutboundConnectionsBlocked takes priority. This setting will get applied to Windows releases version 1809 and above. | - |
| PolicyRulesFromGroupPolicyMerged | Write | Boolean | Configures the firewall to merge Firewall Rule policies from group policy with those from local store instead of ignoring the local store rules. When PolicyRulesFromGroupPolicyNotMerged and PolicyRulesFromGroupPolicyMerged are both true, PolicyRulesFromGroupPolicyMerged takes priority. | - |
| PolicyRulesFromGroupPolicyNotMerged | Write | Boolean | Configures the firewall to prevent merging Firewall Rule policies from group policy with those from local store instead of ignoring the local store rules. When PolicyRulesFromGroupPolicyNotMerged and PolicyRulesFromGroupPolicyMerged are both true, PolicyRulesFromGroupPolicyMerged takes priority. | - |
| SecuredPacketExemptionAllowed | Write | Boolean | Configures the firewall to allow the host computer to respond to unsolicited network traffic of that traffic is secured by IPSec even when stealthModeBlocked is set to true. When SecuredPacketExemptionBlocked and SecuredPacketExemptionAllowed are both true, SecuredPacketExemptionAllowed takes priority. | - |
| SecuredPacketExemptionBlocked | Write | Boolean | Configures the firewall to block the host computer to respond to unsolicited network traffic of that traffic is secured by IPSec even when stealthModeBlocked is set to true. When SecuredPacketExemptionBlocked and SecuredPacketExemptionAllowed are both true, SecuredPacketExemptionAllowed takes priority. | - |
| StealthModeBlocked | Write | Boolean | Prevent the server from operating in stealth mode. When StealthModeRequired and StealthModeBlocked are both true, StealthModeBlocked takes priority. | - |
| StealthModeRequired | Write | Boolean | Allow the server to operate in stealth mode. When StealthModeRequired and StealthModeBlocked are both true, StealthModeBlocked takes priority. | - |
| UnicastResponsesToMulticastBroadcastsBlocked | Write | Boolean | Configures the firewall to block unicast responses to multicast broadcast traffic. When UnicastResponsesToMulticastBroadcastsRequired and UnicastResponsesToMulticastBroadcastsBlocked are both true, UnicastResponsesToMulticastBroadcastsBlocked takes priority. | - |
| UnicastResponsesToMulticastBroadcastsRequired | Write | Boolean | Configures the firewall to allow unicast responses to multicast broadcast traffic. When UnicastResponsesToMulticastBroadcastsRequired and UnicastResponsesToMulticastBroadcastsBlocked are both true, UnicastResponsesToMulticastBroadcastsBlocked takes priority. | - |

#### MSFT\_MicrosoftGraphWindowsFirewallRule

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Action | Write | String | The action the rule enforces. If not specified, the default is Allowed. Possible values are: notConfigured, blocked, allowed. | `notConfigured`, `blocked`, `allowed` |
| Description | Write | String | The description of the rule. | - |
| DisplayName | Write | String | The display name of the rule. Does not need to be unique. | - |
| EdgeTraversal | Write | String | Indicates whether edge traversal is enabled or disabled for this rule. The EdgeTraversal setting indicates that specific inbound traffic is allowed to tunnel through NATs and other edge devices using the Teredo tunneling technology. In order for this setting to work correctly, the application or service with the inbound firewall rule needs to support IPv6. The primary application of this setting allows listeners on the host to be globally addressable through a Teredo IPv6 address. New rules have the EdgeTraversal property disabled by default. Possible values are: notConfigured, blocked, allowed. | `notConfigured`, `blocked`, `allowed` |
| FilePath | Write | String | The full file path of an app that's affected by the firewall rule. | - |
| InterfaceTypes | Write | StringArray\[\] | The interface types of the rule. Possible values are: notConfigured, remoteAccess, wireless, lan. | `notConfigured`, `remoteAccess`, `wireless`, `lan` |
| LocalAddressRanges | Write | StringArray\[\] | List of local addresses covered by the rule. Default is any address. Valid tokens include:'' indicates any local address. If present, this must be the only token included.A subnet can be specified using either the subnet mask or network prefix notation. If neither a subnet mask nor a network prefix is specified, the subnet mask defaults to 255.255.255.255.A valid IPv6 address.An IPv4 address range in the format of 'start address - end address' with no spaces included.An IPv6 address range in the format of 'start address - end address' with no spaces included. | - |
| LocalPortRanges | Write | StringArray\[\] | List of local port ranges. For example, '100-120', '200', '300-320'. If not specified, the default is All. | - |
| LocalUserAuthorizations | Write | String | Specifies the list of authorized local users for the app container. This is a string in Security Descriptor Definition Language \(SDDL\) format. | - |
| PackageFamilyName | Write | String | The package family name of a Microsoft Store application that's affected by the firewall rule. | - |
| ProfileTypes | Write | String | Specifies the profiles to which the rule belongs. If not specified, the default is All. Possible values are: notConfigured, domain, private, public. | - |
| Protocol | Write | UInt32 | 0-255 number representing the IP protocol \(TCP = 6, UDP = 17\). If not specified, the default is All. Valid values 0 to 255 | - |
| RemoteAddressRanges | Write | StringArray\[\] | List of tokens specifying the remote addresses covered by the rule. Tokens are case insensitive. Default is any address. Valid tokens include:'' indicates any remote address. If present, this must be the only token included.'Defaultgateway''DHCP''DNS''WINS''Intranet' \(supported on Windows versions 1809+\)'RmtIntranet' \(supported on Windows versions 1809+\)'Internet' \(supported on Windows versions 1809+\)'Ply2Renders' \(supported on Windows versions 1809+\)'LocalSubnet' indicates any local address on the local subnet.A subnet can be specified using either the subnet mask or network prefix notation. If neither a subnet mask nor a network prefix is specified, the subnet mask defaults to 255.255.255.255.A valid IPv6 address.An IPv4 address range in the format of 'start address - end address' with no spaces included.An IPv6 address range in the format of 'start address - end address' with no spaces included. | - |
| RemotePortRanges | Write | StringArray\[\] | List of remote port ranges. For example, '100-120', '200', '300-320'. If not specified, the default is All. | - |
| ServiceName | Write | String | The name used in cases when a service, not an application, is sending or receiving traffic. | - |
| TrafficDirection | Write | String | The traffic direction that the rule is enabled for. If not specified, the default is Out. Possible values are: notConfigured, out, in. | `notConfigured`, `out`, `in` |

#### MSFT\_MicrosoftGraphDeviceManagementUserRightsSetting

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| LocalUsersOrGroups | Write | MSFT\_MicrosoftGraphDeviceManagementUserRightsLocalUserOrGroup\[\] | Representing a collection of local users or groups which will be set on device if the state of this setting is Allowed. This collection can contain a maximum of 500 elements. | - |
| State | Write | String | Representing the current state of this user rights setting. Possible values are: notConfigured, blocked, allowed. | `notConfigured`, `blocked`, `allowed` |

#### MSFT\_MicrosoftGraphDeviceManagementUserRightsLocalUserOrGroup

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Description | Write | String | Admins description of this local user or group. | - |
| Name | Write | String | The name of this local user or group. | - |
| SecurityIdentifier | Write | String | The security identifier of this local user or group \(e.g. S-1-5-32-544\). | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationFirmwareInterfacePolicyWindows10 resource type

### Description

Intune Device Configuration Firmware Interface Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Bluetooth | Write | String | Defines whether a user is allowed to enable Bluetooth. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| BootFromBuiltInNetworkAdapters | Write | String | Defines whether a user is allowed to boot from built-in network adapters. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| BootFromExternalMedia | Write | String | Defines whether a user is allowed to boot from external media. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| Cameras | Write | String | Defines whether built-in cameras are enabled. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| ChangeUefiSettingsPermission | Write | String | Defines the permission level granted to users to change UEFI settings. Possible values are: notConfiguredOnly, none. | `notConfiguredOnly`, `none` |
| FrontCamera | Write | String | Defines whether a user is allowed to enable Front Camera. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| InfraredCamera | Write | String | Defines whether a user is allowed to enable Infrared camera. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| Microphone | Write | String | Defines whether a user is allowed to enable Microphone. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| MicrophonesAndSpeakers | Write | String | Defines whether built-in microphones or speakers are enabled. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| NearFieldCommunication | Write | String | Defines whether a user is allowed to enable Near Field Communication. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| Radios | Write | String | Defines whether built-in radios e.g. WIFI, NFC, Bluetooth, are enabled. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| RearCamera | Write | String | Defines whether a user is allowed to enable rear camera. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| SdCard | Write | String | Defines whether a user is allowed to enable SD Card Port. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| SimultaneousMultiThreading | Write | String | Defines whether a user is allowed to enable Simultaneous MultiThreading. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| UsbTypeAPort | Write | String | Defines whether a user is allowed to enable USB Type A Port. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| VirtualizationOfCpuAndIO | Write | String | Defines whether CPU and IO virtualization is enabled. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| WakeOnLAN | Write | String | Defines whether a user is allowed to enable Wake on LAN. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| WakeOnPower | Write | String | Defines whether a user is allowed to enable Wake On Power. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| WiFi | Write | String | Defines whether a user is allowed to enable WiFi. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| WindowsPlatformBinaryTable | Write | String | Defines whether a user is allowed to enable Windows Platform Binary Table. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| WirelessWideAreaNetwork | Write | String | Defines whether a user is allowed to enable Wireless Wide Area Network. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| SupportsScopeTags | Write | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationHealthMonitoringConfigurationPolicyWindows10 resource type

### Description

Intune Device Configuration Health Monitoring Configuration Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AllowDeviceHealthMonitoring | Write | String | Enables device health monitoring on the device. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| ConfigDeviceHealthMonitoringCustomScope | Write | String | Specifies custom set of events collected from the device where health monitoring is enabled | - |
| ConfigDeviceHealthMonitoringScope | Write | StringArray\[\] | Specifies set of events collected from the device where health monitoring is enabled. Possible values are: undefined, healthMonitoring, bootPerformance, windowsUpdates, privilegeManagement. | `undefined`, `healthMonitoring`, `bootPerformance`, `windowsUpdates`, `privilegeManagement` |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| SupportsScopeTags | Write | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationIdentityProtectionPolicyWindows10 resource type

### Description

Intune Device Configuration Identity Protection Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| EnhancedAntiSpoofingForFacialFeaturesEnabled | Write | Boolean | Boolean value used to enable enhanced anti-spoofing for facial feature recognition on Windows Hello face authentication. | - |
| PinExpirationInDays | Write | UInt32 | Integer value specifies the period \(in days\) that a PIN can be used before the system requires the user to change it. Valid values are 0 to 730 inclusive. Valid values 0 to 730 | - |
| PinLowercaseCharactersUsage | Write | String | This value configures the use of lowercase characters in the Windows Hello for Business PIN. Possible values are: blocked, required, allowed, notConfigured. | `blocked`, `required`, `allowed`, `notConfigured` |
| PinMaximumLength | Write | UInt32 | Integer value that sets the maximum number of characters allowed for the work PIN. Valid values are 4 to 127 inclusive and greater than or equal to the value set for the minimum PIN. Valid values 4 to 127 | - |
| PinMinimumLength | Write | UInt32 | Integer value that sets the minimum number of characters required for the Windows Hello for Business PIN. Valid values are 4 to 127 inclusive and less than or equal to the value set for the maximum PIN. Valid values 4 to 127 | - |
| PinPreviousBlockCount | Write | UInt32 | Controls the ability to prevent users from using past PINs. This must be set between 0 and 50, inclusive, and the current PIN of the user is included in that count. If set to 0, previous PINs are not stored. PIN history is not preserved through a PIN reset. Valid values 0 to 50 | - |
| PinRecoveryEnabled | Write | Boolean | Boolean value that enables a user to change their PIN by using the Windows Hello for Business PIN recovery service. | - |
| PinSpecialCharactersUsage | Write | String | Controls the ability to use special characters in the Windows Hello for Business PIN. Possible values are: blocked, required, allowed, notConfigured. | `blocked`, `required`, `allowed`, `notConfigured` |
| PinUppercaseCharactersUsage | Write | String | This value configures the use of uppercase characters in the Windows Hello for Business PIN. Possible values are: blocked, required, allowed, notConfigured. | `blocked`, `required`, `allowed`, `notConfigured` |
| SecurityDeviceRequired | Write | Boolean | Controls whether to require a Trusted Platform Module \(TPM\) for provisioning Windows Hello for Business. A TPM provides an additional security benefit in that data stored on it can't be used on other devices. If set to False, all devices can provision Windows Hello for Business even if there's not a usable TPM. | - |
| UnlockWithBiometricsEnabled | Write | Boolean | Controls the use of biometric gestures, such as face and fingerprint, as an alternative to the Windows Hello for Business PIN. If set to False, biometric gestures are not allowed. Users must still configure a PIN as a backup in case of failures. | - |
| UseCertificatesForOnPremisesAuthEnabled | Write | Boolean | Boolean value that enables Windows Hello for Business to use certificates to authenticate on-premise resources. | - |
| UseSecurityKeyForSignin | Write | Boolean | Boolean value used to enable the Windows Hello security key as a logon credential. | - |
| WindowsHelloForBusinessBlocked | Write | Boolean | Boolean value that blocks Windows Hello for Business as a method for signing into Windows. | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| SupportsScopeTags | Write | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationImportedPfxCertificatePolicyWindows10 resource type

### Description

Intune Device Configuration Imported Pfx Certificate Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IntendedPurpose | Write | String | Intended Purpose of the Certificate Profile - which could be Unassigned, SmimeEncryption, SmimeSigning etc. Possible values are: unassigned, smimeEncryption, smimeSigning, vpn, wifi. | `unassigned`, `smimeEncryption`, `smimeSigning`, `vpn`, `wifi` |
| CertificateValidityPeriodScale | Write | String | Scale for the Certificate Validity Period. Possible values are: days, months, years. | `days`, `months`, `years` |
| CertificateValidityPeriodValue | Write | UInt32 | Value for the Certificate Validity Period | - |
| KeyStorageProvider | Write | String | Key Storage Provider \(KSP\). Possible values are: useTpmKspOtherwiseUseSoftwareKsp, useTpmKspOtherwiseFail, usePassportForWorkKspOtherwiseFail, useSoftwareKsp. | `useTpmKspOtherwiseUseSoftwareKsp`, `useTpmKspOtherwiseFail`, `usePassportForWorkKspOtherwiseFail`, `useSoftwareKsp` |
| RenewalThresholdPercentage | Write | UInt32 | Certificate renewal threshold percentage. Valid values 1 to 99 | - |
| SubjectAlternativeNameType | Write | String | Certificate Subject Alternative Name Type. Possible values are: none, emailAddress, userPrincipalName, customAzureADAttribute, domainNameService, universalResourceIdentifier. | `none`, `emailAddress`, `userPrincipalName`, `customAzureADAttribute`, `domainNameService`, `universalResourceIdentifier` |
| SubjectNameFormat | Write | String | Certificate Subject Name Format. Possible values are: commonName, commonNameIncludingEmail, commonNameAsEmail, custom, commonNameAsIMEI, commonNameAsSerialNumber, commonNameAsAadDeviceId, commonNameAsIntuneDeviceId, commonNameAsDurableDeviceId. | `commonName`, `commonNameIncludingEmail`, `commonNameAsEmail`, `custom`, `commonNameAsIMEI`, `commonNameAsSerialNumber`, `commonNameAsAadDeviceId`, `commonNameAsIntuneDeviceId`, `commonNameAsDurableDeviceId` |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationKioskPolicyWindows10 resource type

### Description

Intune Device Configuration Kiosk Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| EdgeKioskEnablePublicBrowsing | Write | Boolean | Enable public browsing kiosk mode for the Microsoft Edge browser. The Default is false. | - |
| KioskBrowserBlockedUrlExceptions | Write | StringArray\[\] | Specify URLs that the kiosk browser is allowed to navigate to | - |
| KioskBrowserBlockedURLs | Write | StringArray\[\] | Specify URLs that the kiosk browsers should not navigate to | - |
| KioskBrowserDefaultUrl | Write | String | Specify the default URL the browser should navigate to on launch. | - |
| KioskBrowserEnableEndSessionButton | Write | Boolean | Enable the kiosk browser's end session button. By default, the end session button is disabled. | - |
| KioskBrowserEnableHomeButton | Write | Boolean | Enable the kiosk browser's home button. By default, the home button is disabled. | - |
| KioskBrowserEnableNavigationButtons | Write | Boolean | Enable the kiosk browser's navigation buttons\(forward/back\). By default, the navigation buttons are disabled. | - |
| KioskBrowserRestartOnIdleTimeInMinutes | Write | UInt32 | Specify the number of minutes the session is idle until the kiosk browser restarts in a fresh state. Valid values are 1-1440. Valid values 1 to 1440 | - |
| KioskProfiles | Write | MSFT\_MicrosoftGraphwindowsKioskProfile\[\] | This policy setting allows to define a list of Kiosk profiles for a Kiosk configuration. This collection can contain a maximum of 3 elements. | - |
| WindowsKioskForceUpdateSchedule | Write | MSFT\_MicrosoftGraphwindowsKioskForceUpdateSchedule | force update schedule for Kiosk devices. | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphWindowsKioskProfile

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AppConfiguration | Write | MSFT\_MicrosoftGraphWindowsKioskAppConfiguration | The App configuration that will be used for this kiosk configuration. | - |
| ProfileId | Write | String | Key of the entity. | - |
| ProfileName | Write | String | This is a friendly nameused to identify a group of applications, the layout of these apps on the start menu and the users to whom this kiosk configuration is assigned. | - |
| UserAccountsConfiguration | Write | MSFT\_MicrosoftGraphWindowsKioskUser\[\] | The user accounts that will be locked to this kiosk configuration. This collection can contain a maximum of 100 elements. | - |

#### MSFT\_MicrosoftGraphWindowsKioskAppConfiguration

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AllowAccessToDownloadsFolder | Write | Boolean | This setting allows access to Downloads folder in file explorer. | - |
| Apps | Write | MSFT\_MicrosoftGraphWindowsKioskAppBase\[\] | These are the only Windows Store Apps that will be available to launch from the Start menu. This collection can contain a maximum of 128 elements. | - |
| DisallowDesktopApps | Write | Boolean | This setting indicates that desktop apps are allowed. Default to true. | - |
| ShowTaskBar | Write | Boolean | This setting allows the admin to specify whether the Task Bar is shown or not. | - |
| StartMenuLayoutXml | Write | String | Allows admins to override the default Start layout and prevents the user from changing it.The layout is modified by specifying an XML file based on a layout modification schema. XML needs to be in Binary format. | - |
| UwpApp | Write | MSFT\_MicrosoftGraphWindowsKioskUWPApp | This is the only Application User Model ID \(AUMID\) that will be available to launch use while in Kiosk Mode | - |
| Win32App | Write | MSFT\_MicrosoftGraphWindowsKioskWin32App | This is the win32 app that will be available to launch use while in Kiosk Mode | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.windowsKioskMultipleApps`, `#microsoft.graph.windowsKioskSingleUWPApp`, `#microsoft.graph.windowsKioskSingleWin32App` |

#### MSFT\_MicrosoftGraphWindowsKioskAppBase

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AppType | Write | String | The app type. Possible values are: unknown, store, desktop, aumId. | `unknown`, `store`, `desktop`, `aumId` |
| AutoLaunch | Write | Boolean | Allow the app to be auto-launched in multi-app kiosk mode | - |
| Name | Write | String | Represents the friendly name of an app | - |
| StartLayoutTileSize | Write | String | The app tile size for the start layout. Possible values are: hidden, small, medium, wide, large. | `hidden`, `small`, `medium`, `wide`, `large` |
| DesktopApplicationId | Write | String | Define the DesktopApplicationID of the app | - |
| DesktopApplicationLinkPath | Write | String | Define the DesktopApplicationLinkPath of the app | - |
| Path | Write | String | Define the path of a desktop app | - |
| AppId | Write | String | This references an Intune App that will be target to the same assignments as Kiosk configuration | - |
| AppUserModelId | Write | String | This is the only Application User Model ID \(AUMID\) that will be available to launch use while in Kiosk Mode | - |
| ContainedAppId | Write | String | This references an contained App from an Intune App | - |
| ClassicAppPath | Write | String | This is the classicapppath to be used by v4 Win32 app while in Kiosk Mode | - |
| EdgeKiosk | Write | String | Edge kiosk \(url\) for Edge kiosk mode | - |
| EdgeKioskIdleTimeoutMinutes | Write | UInt32 | Edge kiosk idle timeout in minutes for Edge kiosk mode. Valid values 0 to 1440 | - |
| EdgeKioskType | Write | String | Edge kiosk type for Edge kiosk mode. Possible values are: publicBrowsing, fullScreen. | `publicBrowsing`, `fullScreen` |
| EdgeNoFirstRun | Write | Boolean | Edge first run flag for Edge kiosk mode | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.windowsKioskDesktopApp`, `#microsoft.graph.windowsKioskUWPApp`, `#microsoft.graph.windowsKioskWin32App` |

#### MSFT\_MicrosoftGraphWindowsKioskUWPApp

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AppId | Write | String | This references an Intune App that will be target to the same assignments as Kiosk configuration | - |
| AppUserModelId | Write | String | This is the only Application User Model ID \(AUMID\) that will be available to launch use while in Kiosk Mode | - |
| ContainedAppId | Write | String | This references an contained App from an Intune App | - |
| AppType | Write | String | The app type. Possible values are: unknown, store, desktop, aumId. | `unknown`, `store`, `desktop`, `aumId` |
| AutoLaunch | Write | Boolean | Allow the app to be auto-launched in multi-app kiosk mode | - |
| Name | Write | String | Represents the friendly name of an app | - |
| StartLayoutTileSize | Write | String | The app tile size for the start layout. Possible values are: hidden, small, medium, wide, large. | `hidden`, `small`, `medium`, `wide`, `large` |
| DesktopApplicationId | Write | String | Define the DesktopApplicationID of the app | - |
| DesktopApplicationLinkPath | Write | String | Define the DesktopApplicationLinkPath of the app | - |
| Path | Write | String | Define the path of a desktop app | - |
| ClassicAppPath | Write | String | This is the classicapppath to be used by v4 Win32 app while in Kiosk Mode | - |
| EdgeKiosk | Write | String | Edge kiosk \(url\) for Edge kiosk mode | - |
| EdgeKioskIdleTimeoutMinutes | Write | UInt32 | Edge kiosk idle timeout in minutes for Edge kiosk mode. Valid values 0 to 1440 | - |
| EdgeKioskType | Write | String | Edge kiosk type for Edge kiosk mode. Possible values are: publicBrowsing, fullScreen. | `publicBrowsing`, `fullScreen` |
| EdgeNoFirstRun | Write | Boolean | Edge first run flag for Edge kiosk mode | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.windowsKioskDesktopApp`, `#microsoft.graph.windowsKioskUWPApp`, `#microsoft.graph.windowsKioskWin32App` |

#### MSFT\_MicrosoftGraphWindowsKioskWin32App

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ClassicAppPath | Write | String | This is the classicapppath to be used by v4 Win32 app while in Kiosk Mode | - |
| EdgeKiosk | Write | String | Edge kiosk \(url\) for Edge kiosk mode | - |
| EdgeKioskIdleTimeoutMinutes | Write | UInt32 | Edge kiosk idle timeout in minutes for Edge kiosk mode. Valid values 0 to 1440 | - |
| EdgeKioskType | Write | String | Edge kiosk type for Edge kiosk mode. Possible values are: publicBrowsing, fullScreen. | `publicBrowsing`, `fullScreen` |
| EdgeNoFirstRun | Write | Boolean | Edge first run flag for Edge kiosk mode | - |
| AppType | Write | String | The app type. Possible values are: unknown, store, desktop, aumId. | `unknown`, `store`, `desktop`, `aumId` |
| AutoLaunch | Write | Boolean | Allow the app to be auto-launched in multi-app kiosk mode | - |
| Name | Write | String | Represents the friendly name of an app | - |
| StartLayoutTileSize | Write | String | The app tile size for the start layout. Possible values are: hidden, small, medium, wide, large. | `hidden`, `small`, `medium`, `wide`, `large` |
| DesktopApplicationId | Write | String | Define the DesktopApplicationID of the app | - |
| DesktopApplicationLinkPath | Write | String | Define the DesktopApplicationLinkPath of the app | - |
| Path | Write | String | Define the path of a desktop app | - |
| AppId | Write | String | This references an Intune App that will be target to the same assignments as Kiosk configuration | - |
| AppUserModelId | Write | String | This is the only Application User Model ID \(AUMID\) that will be available to launch use while in Kiosk Mode | - |
| ContainedAppId | Write | String | This references an contained App from an Intune App | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.windowsKioskDesktopApp`, `#microsoft.graph.windowsKioskUWPApp`, `#microsoft.graph.windowsKioskWin32App` |

#### MSFT\_MicrosoftGraphWindowsKioskUser

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| GroupName | Write | String | The name of the AD group that will be locked to this kiosk configuration | - |
| DisplayName | Write | String | The display name of the AzureAD group that will be locked to this kiosk configuration | - |
| GroupId | Write | String | The ID of the AzureAD group that will be locked to this kiosk configuration | - |
| UserId | Write | String | The ID of the AzureAD user that will be locked to this kiosk configuration | - |
| UserPrincipalName | Write | String | The user accounts that will be locked to this kiosk configuration | - |
| UserName | Write | String | The local user that will be locked to this kiosk configuration | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.windowsKioskActiveDirectoryGroup`, `#microsoft.graph.windowsKioskAutologon`, `#microsoft.graph.windowsKioskAzureADGroup`, `#microsoft.graph.windowsKioskAzureADUser`, `#microsoft.graph.windowsKioskLocalGroup`, `#microsoft.graph.windowsKioskLocalUser`, `#microsoft.graph.windowsKioskVisitor` |

#### MSFT\_MicrosoftGraphWindowsKioskForceUpdateSchedule

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DayofMonth | Write | UInt32 | Day of month. Valid values 1 to 31 | - |
| DayofWeek | Write | String | Day of week. Possible values are: sunday, monday, tuesday, wednesday, thursday, friday, saturday. | `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday` |
| Recurrence | Write | String | Recurrence schedule. Possible values are: none, daily, weekly, monthly. | `none`, `daily`, `weekly`, `monthly` |
| RunImmediatelyIfAfterStartDateTime | Write | Boolean | If true, runs the task immediately if StartDateTime is in the past, else, runs at the next recurrence. | - |
| StartDateTime | Write | String | The start time for the force restart. | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationNetworkBoundaryPolicyWindows10 resource type

### Description

Intune Device Configuration Network Boundary Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| WindowsNetworkIsolationPolicy | Write | MSFT\_MicrosoftGraphwindowsNetworkIsolationPolicy | Windows Network Isolation Policy | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| SupportsScopeTags | Write | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphWindowsNetworkIsolationPolicy

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| EnterpriseCloudResources | Write | MSFT\_MicrosoftGraphProxiedDomain1\[\] | Contains a list of enterprise resource domains hosted in the cloud that need to be protected. Connections to these resources are considered enterprise data. If a proxy is paired with a cloud resource, traffic to the cloud resource will be routed through the enterprise network via the denoted proxy server \(on Port 80\). A proxy server used for this purpose must also be configured using the EnterpriseInternalProxyServers policy. This collection can contain a maximum of 500 elements. | - |
| EnterpriseInternalProxyServers | Write | StringArray\[\] | This is the comma-separated list of internal proxy servers. For example, '157.54.14.28, 157.54.11.118, 10.202.14.167, 157.53.14.163, 157.69.210.59'. These proxies have been configured by the admin to connect to specific resources on the Internet. They are considered to be enterprise network locations. The proxies are only leveraged in configuring the EnterpriseCloudResources policy to force traffic to the matched cloud resources through these proxies. | - |
| EnterpriseIPRanges | Write | MSFT\_MicrosoftGraphIpRange1\[\] | Sets the enterprise IP ranges that define the computers in the enterprise network. Data that comes from those computers will be considered part of the enterprise and protected. These locations will be considered a safe destination for enterprise data to be shared to. This collection can contain a maximum of 500 elements. | - |
| EnterpriseIPRangesAreAuthoritative | Write | Boolean | Boolean value that tells the client to accept the configured list and not to use heuristics to attempt to find other subnets. Default is false. | - |
| EnterpriseNetworkDomainNames | Write | StringArray\[\] | This is the list of domains that comprise the boundaries of the enterprise. Data from one of these domains that is sent to a device will be considered enterprise data and protected. These locations will be considered a safe destination for enterprise data to be shared to. | - |
| EnterpriseProxyServers | Write | StringArray\[\] | This is a list of proxy servers. Any server not on this list is considered non-enterprise. | - |
| EnterpriseProxyServersAreAuthoritative | Write | Boolean | Boolean value that tells the client to accept the configured list of proxies and not try to detect other work proxies. Default is false | - |
| NeutralDomainResources | Write | StringArray\[\] | List of domain names that can used for work or personal resource. | - |

#### MSFT\_MicrosoftGraphProxiedDomain1

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IpAddressOrFQDN | Write | String | The IP address or FQDN | - |
| Proxy | Write | String | Proxy IP or FQDN | - |

#### MSFT\_MicrosoftGraphIpRange1

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| CidrAddress | Write | String | IPv4 address in CIDR notation. Not nullable. | - |
| LowerAddress | Write | String | Lower address. | - |
| UpperAddress | Write | String | Upper address. | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.iPv4CidrRange`, `#microsoft.graph.iPv6CidrRange`, `#microsoft.graph.iPv4Range`, `#microsoft.graph.iPv6Range` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationPkcsCertificatePolicyWindows10 resource type

### Description

Intune Device Configuration Pkcs Certificate Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| CertificateStore | Write | String | Target store certificate. Possible values are: user, machine. | `user`, `machine` |
| CertificateTemplateName | Write | String | PKCS Certificate Template Name | - |
| CertificationAuthority | Write | String | PKCS Certification Authority | - |
| CertificationAuthorityName | Write | String | PKCS Certification Authority Name | - |
| CustomSubjectAlternativeNames | Write | MSFT\_MicrosoftGraphcustomSubjectAlternativeName\[\] | Custom Subject Alternative Name Settings. This collection can contain a maximum of 500 elements. | - |
| ExtendedKeyUsages | Write | MSFT\_MicrosoftGraphextendedKeyUsage\[\] | Extended Key Usage \(EKU\) settings. This collection can contain a maximum of 500 elements. | - |
| SubjectAlternativeNameFormatString | Write | String | Custom String that defines the AAD Attribute. | - |
| SubjectNameFormatString | Write | String | Custom format to use with SubjectNameFormat = Custom. Example: CN=EmailAddress}},E=EmailAddress}},OU=Enterprise Users,O=Contoso Corporation,L=Redmond,ST=WA,C=US | - |
| CertificateValidityPeriodScale | Write | String | Scale for the Certificate Validity Period. Possible values are: days, months, years. | `days`, `months`, `years` |
| CertificateValidityPeriodValue | Write | UInt32 | Value for the Certificate Validity Period | - |
| KeyStorageProvider | Write | String | Key Storage Provider \(KSP\). Possible values are: useTpmKspOtherwiseUseSoftwareKsp, useTpmKspOtherwiseFail, usePassportForWorkKspOtherwiseFail, useSoftwareKsp. | `useTpmKspOtherwiseUseSoftwareKsp`, `useTpmKspOtherwiseFail`, `usePassportForWorkKspOtherwiseFail`, `useSoftwareKsp` |
| RenewalThresholdPercentage | Write | UInt32 | Certificate renewal threshold percentage. Valid values 1 to 99 | - |
| SubjectAlternativeNameType | Write | String | Certificate Subject Alternative Name Type. Possible values are: none, emailAddress, userPrincipalName, customAzureADAttribute, domainNameService, universalResourceIdentifier. | `none`, `emailAddress`, `userPrincipalName`, `customAzureADAttribute`, `domainNameService`, `universalResourceIdentifier` |
| SubjectNameFormat | Write | String | Certificate Subject Name Format. Possible values are: commonName, commonNameIncludingEmail, commonNameAsEmail, custom, commonNameAsIMEI, commonNameAsSerialNumber, commonNameAsAadDeviceId, commonNameAsIntuneDeviceId, commonNameAsDurableDeviceId. | `commonName`, `commonNameIncludingEmail`, `commonNameAsEmail`, `custom`, `commonNameAsIMEI`, `commonNameAsSerialNumber`, `commonNameAsAadDeviceId`, `commonNameAsIntuneDeviceId`, `commonNameAsDurableDeviceId` |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphCustomSubjectAlternativeName

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Write | String | Custom SAN Name | - |
| SanType | Write | String | Custom SAN Type. Possible values are: none, emailAddress, userPrincipalName, customAzureADAttribute, domainNameService, universalResourceIdentifier. | `none`, `emailAddress`, `userPrincipalName`, `customAzureADAttribute`, `domainNameService`, `universalResourceIdentifier` |

#### MSFT\_MicrosoftGraphExtendedKeyUsage

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Write | String | Extended Key Usage Name | - |
| ObjectIdentifier | Write | String | Extended Key Usage Object Identifier | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationPolicyAndroidDeviceAdministrator resource type

### Description

This resource configures the settings of Android Device Administrator device restriction policy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune policy. | - |
| DisplayName | Key | String | Display name of the Intune policy. | - |
| Description | Write | String | Description of the Intune policy. | - |
| AppsBlockClipboardSharing | Write | Boolean | Block clipboard sharing between apps \(Samsung KNOX Standard 4.0+\). | - |
| AppsBlockCopyPaste | Write | Boolean | Block copy and paste functionality. | - |
| AppsBlockYouTube | Write | Boolean | Block YouTube \(Samsung KNOX Standard 4.0+\). | - |
| AppsHideList | Write | MSFT\_MicrosoftGraphapplistitem\[\] | Specify the apps that will be hidden on the device. Users can't discover or run these apps. | - |
| AppsInstallAllowList | Write | MSFT\_MicrosoftGraphapplistitem\[\] | Specify the apps that users can install. Users will not be able to install apps that are not on the list. | - |
| AppsLaunchBlockList | Write | MSFT\_MicrosoftGraphapplistitem\[\] | Specify the apps that users can't run on their device. | - |
| BluetoothBlocked | Write | Boolean | Block Bluetooth \(Samsung KNOX Standard 4.0+\). | - |
| CameraBlocked | Write | Boolean | Block use of camera | - |
| CellularBlockDataRoaming | Write | Boolean | Block data roaming over the cellular network \(Samsung KNOX Standard 4.0+\). | - |
| CellularBlockMessaging | Write | Boolean | Block SMS/MMS messaging functionality \(Samsung KNOX Standard 4.0+\). | - |
| CellularBlockVoiceRoaming | Write | Boolean | Block voice roaming over the cellular network \(Samsung KNOX Standard 4.0+\). | - |
| CellularBlockWiFiTethering | Write | Boolean | Block Wi-Fi tethering \(Samsung KNOX Standard 4.0+\). | - |
| CompliantAppListType | Write | String | Device compliance can be viewed in the Restricted Apps Compliance report. | `none`, `appsInListCompliant`, `appsNotInListCompliant` |
| CompliantAppsList | Write | MSFT\_MicrosoftGraphapplistitem\[\] | Enter the Google Play Store URL of the app you want. For example, to specify the Microsoft Remote Desktop app for Android, enter [https://play.google.com/store/apps/details?id=com.microsoft.rdc.android](https://play.google.com/store/apps/details?id=com.microsoft.rdc.android). To find the URL of an app, use a search engine to locate the store page. For example, to find the Remote Desktop app, you could search Microsoft Remote Desktop Play Store. | - |
| DateAndTimeBlockChanges | Write | Boolean | Block user from changing date and time on device \(Samsung KNOX\). | - |
| DeviceSharingAllowed | Write | Boolean | Allow multiple users to log into the Company Portal using their AAD credentials \(Samsung KNOX Standard 4.0+\). | - |
| DiagnosticDataBlockSubmission | Write | Boolean | Block submitting diagnostic data from device. | - |
| FactoryResetBlocked | Write | Boolean | Block factory reset on device. | - |
| GoogleAccountBlockAutoSync | Write | Boolean | Block Google account auto sync functionality on device. | - |
| GooglePlayStoreBlocked | Write | Boolean | Block Google Play store \(Samsung KNOX Standard 4.0+\). | - |
| KioskModeApps | Write | MSFT\_MicrosoftGraphapplistitem\[\] | Kiosk mode apps | - |
| KioskModeBlockSleepButton | Write | Boolean | Kiosk mode block sleep button | - |
| KioskModeBlockVolumeButtons | Write | Boolean | Kiosk mode block volume buttons | - |
| LocationServicesBlocked | Write | Boolean | Location services blocked | - |
| NfcBlocked | Write | Boolean | Block Near Field Communication \(NFC\) technology \(Samsung KNOX Standard 4.0+\). | - |
| PasswordBlockFingerprintUnlock | Write | Boolean | Block using fingerprint to unlock device. | - |
| PasswordBlockTrustAgents | Write | Boolean | Block Smart Lock or other trust agents from adjusting lock screen settings \(Samsung KNOX Standard 5.0+\). | - |
| PasswordExpirationDays | Write | UInt32 | Number of days until device password must be changed. \(1-365\) | - |
| PasswordMinimumLength | Write | UInt32 | Minimum number of digits or characters in password. \(4-16\) | - |
| PasswordMinutesOfInactivityBeforeScreenTimeout | Write | UInt32 | Maximum minutes of inactivity until screen locks. Ignored by device if new time is longer than what's currently set on device. If set to Immediately, devices will use the minimum possible value per device. | - |
| PasswordPreviousPasswordBlockCount | Write | UInt32 | Number of new passwords that must be used until an old one can be reused. | - |
| PasswordRequired | Write | Boolean | Require password to access device. | - |
| PasswordRequiredType | Write | String | Specify the type of password required. | `deviceDefault`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `numeric`, `numericComplex`, `any` |
| PasswordSignInFailureCountBeforeFactoryReset | Write | UInt32 | Number of consecutive times an incorrect password can be entered before device is wiped of all data. | - |
| PowerOffBlocked | Write | Boolean | Block user from powering off device. If this setting is disabled the setting 'Number of sign-in failures before wiping device' does not function. | - |
| RequiredPasswordComplexity | Write | String | Define the password complexity. | `none`, `low`, `medium`, `high` |
| ScreenCaptureBlocked | Write | Boolean | Block capturing contents of screen as an image. | - |
| SecurityRequireVerifyApps | Write | Boolean | Security require verify apps | - |
| StorageBlockGoogleBackup | Write | Boolean | Block sync with Google backup. | - |
| StorageBlockRemovableStorage | Write | Boolean | Block removable storage usage \(Samsung KNOX Standard 4.0+\). | - |
| StorageRequireDeviceEncryption | Write | Boolean | Require encryption on device. Not all devices support encryption. | - |
| StorageRequireRemovableStorageEncryption | Write | Boolean | Storage cards must be encrypted. Not all devices support storage card encryption. For more information, see the device and mobile operating system documentation. | - |
| VoiceAssistantBlocked | Write | Boolean | Block voice assistant \(Samsung KNOX Standard 4.0+\). | - |
| VoiceDialingBlocked | Write | Boolean | Block voice dialing \(Samsung KNOX Standard 4.0+\). | - |
| WebBrowserBlockAutofill | Write | Boolean | Block autofill. | - |
| WebBrowserBlocked | Write | Boolean | Block web browser on device. | - |
| WebBrowserBlockJavaScript | Write | Boolean | Block JavaScript in the browser. | - |
| WebBrowserBlockPopups | Write | Boolean | Block pop-ups in web browser. | - |
| WebBrowserCookieSettings | Write | String | Allow or block browser cookies | `browserDefault`, `blockAlways`, `allowCurrentWebSite`, `allowFromWebsitesVisited`, `allowAlways` |
| WiFiBlocked | Write | Boolean | Block Wi-Fi \(Samsung KNOX Standard 4.0+\). | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphapplistitem

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | odatatype of the item. | `#microsoft.graph.appleAppListItem` |
| appId | Write | String | Kiosk mode managed app id | - |
| appStoreUrl | Write | String | Define the app store URL. | - |
| name | Write | String | Define the name of the app. | - |
| publisher | Write | String | Define the publisher of the app. | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | DeviceManagementConfiguration.Read.All |
| Update | DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationPolicyAndroidDeviceOwner resource type

### Description

This resource configures an Intune Device Configuration Policy Android Device Owner.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The Id of the policy. | - |
| DisplayName | Key | String | The display name of hte policy. | - |
| Description | Write | String | The description of the policy. | - |
| AccountsBlockModification | Write | Boolean | Block modification of accounts. Only supported on Dedicated devices. | - |
| AppsAllowInstallFromUnknownSources | Write | Boolean | When allowed, users can enable the 'unknown sources' setting to install apps from sources other than the Google Play Store. | - |
| AppsAutoUpdatePolicy | Write | String | Devices check for app updates daily. The default behavior is to let device users decide. They'll be able to set their preferences in the managed Google Play app. | `notConfigured`, `userChoice`, `never`, `wiFiOnly`, `always` |
| AppsDefaultPermissionPolicy | Write | String | Define the default permission policy for requests for runtime permissions. | `deviceDefault`, `prompt`, `autoGrant`, `autoDeny` |
| AppsRecommendSkippingFirstUseHints | Write | Boolean | Enable a suggestion to apps that they skip their user tutorials and any introductory hints when they first start up, if applicable. | - |
| AzureAdSharedDeviceDataClearApps | Write | MSFT\_MicrosoftGraphapplistitem\[\] | A list of managed apps that will have their data cleared during a global sign-out in AAD shared device mode. This collection can contain a maximum of 500 elements. | - |
| BluetoothBlockConfiguration | Write | Boolean | Block configuring Bluetooth. | - |
| BluetoothBlockContactSharing | Write | Boolean | Block access to work contacts from another device such as a car system when an Android device is paired via Bluetooth. | - |
| CameraBlocked | Write | Boolean | Block all cameras on the device | - |
| CellularBlockWiFiTethering | Write | Boolean | Block tethering and access to portable hotspots. | - |
| CertificateCredentialConfigurationDisabled | Write | Boolean | Blocks users from making any changes to credentials associated with certificates associated with certificates assigned to them. | - |
| CrossProfilePoliciesAllowCopyPaste | Write | Boolean | Indicates whether or not text copied from one profile \(personal or work\) can be pasted in the other. | - |
| CrossProfilePoliciesAllowDataSharing | Write | String | Indicates whether data from one profile \(personal or work\) can be shared with apps in the other profile. | `notConfigured`, `crossProfileDataSharingBlocked`, `dataSharingFromWorkToPersonalBlocked`, `crossProfileDataSharingAllowed`, `unkownFutureValue` |
| CrossProfilePoliciesShowWorkContactsInPersonalProfile | Write | Boolean | Indicates whether or not contacts stored in work profile are shown in personal profile contact searches/incoming calls. | - |
| DataRoamingBlocked | Write | Boolean | Block data roaming. | - |
| DateTimeConfigurationBlocked | Write | Boolean | Block user from manually setting the date and time. | - |
| DetailedHelpText | Write | MSFT\_MicrosoftGraphandroiddeviceowneruserfacingmessage | Represents the customized detailed help text provided to users when they attempt to modify managed settings on their device. | - |
| DeviceOwnerLockScreenMessage | Write | MSFT\_MicrosoftGraphandroiddeviceowneruserfacingmessage | Represents the customized lock screen message provided to users when they attempt to modify managed settings on their device. | - |
| EnrollmentProfile | Write | String | Represents the enrollment profile type. | `notConfigured`, `dedicatedDevice`, `fullyManaged` |
| FactoryResetBlocked | Write | Boolean | Block factory resetting from settings. | - |
| FactoryResetDeviceAdministratorEmails | Write | StringArray\[\] | Email addresses of device admins for factory reset protection. When a device is factory reset, it will require that one of these admins log in with their Google account to unlock the device. If none are specified, factory reset protection is not enabled. | - |
| GlobalProxy | Write | MSFT\_MicrosoftGraphandroiddeviceownerglobalproxy | Proxy is set up directly with host, port and excluded hosts. | - |
| GoogleAccountsBlocked | Write | Boolean | Blocking prevents users from adding their personal Google account to their device. | - |
| KioskCustomizationDeviceSettingsBlocked | Write | Boolean | Indicates whether a user can access the device's Settings app while in Kiosk Mode. | - |
| KioskCustomizationPowerButtonActionsBlocked | Write | Boolean | Whether the power menu is shown when a user long presses the Power button of a device in Kiosk Mode. | - |
| KioskCustomizationStatusBar | Write | String | Indicates whether system info and notifications are disabled in Kiosk Mode | `notConfigured`, `notificationsAndSystemInfoEnabled`, `systemInfoOnly` |
| KioskCustomizationSystemErrorWarnings | Write | Boolean | Indicates whether system error dialogs for crashed or unresponsive apps are shown in Kiosk Mode. | - |
| KioskCustomizationSystemNavigation | Write | String | Indicates which navigation features are enabled in Kiosk Mode. | `notConfigured`, `navigationEnabled`, `homeButtonOnly` |
| KioskModeAppOrderEnabled | Write | Boolean | Whether or not to enable app ordering in Kiosk Mode. | - |
| KioskModeAppPositions | Write | MSFT\_MicrosoftGraphandroiddeviceownerkioskmodeapppositionitem\[\] | The ordering of items on Kiosk Mode Managed Home Screen. This collection can contain a maximum of 500 elements. | - |
| KioskModeApps | Write | MSFT\_MicrosoftGraphapplistitem\[\] | A list of managed apps that will be shown when the device is in Kiosk Mode. This collection can contain a maximum of 500 elements. | - |
| KioskModeAppsInFolderOrderedByName | Write | Boolean | Whether or not to alphabetize applications within a folder in Kiosk Mode. | - |
| KioskModeBluetoothConfigurationEnabled | Write | Boolean | Enable end-users to configure and pair devices over Bluetooth. | - |
| KioskModeDebugMenuEasyAccessEnabled | Write | Boolean | Whether or not to allow a user to easy access to the debug menu in Kiosk Mode | - |
| KioskModeExitCode | Write | String | The 4-6 digit PIN will be the code an IT administrator enters on a multi-app dedicated device to pause kiosk mode. | - |
| KioskModeFlashlightConfigurationEnabled | Write | Boolean | Whether or not to allow a user to use the flashlight in Kiosk Mode. | - |
| KioskModeFolderIcon | Write | String | Folder icon configuration for managed home screen in Kiosk Mode. | `notConfigured`, `darkSquare`, `darkCircle`, `lightSquare`, `lightCircle` |
| KioskModeGridHeight | Write | UInt32 | Number of rows for Managed Home Screen grid with app ordering enabled in Kiosk Mode. Valid values 1 to 9999999. | - |
| KioskModeGridWidth | Write | UInt32 | Number of columns for Managed Home Screen grid with app ordering enabled in Kiosk Mode. Valid values 1 to 9999999. | - |
| KioskModeIconSize | Write | String | Icon size configuration for managed home screen in Kiosk Mode. | `notConfigured`, `smallest`, `small`, `regular`, `large`, `largest` |
| KioskModeLockHomeScreen | Write | Boolean | Whether or not to lock home screen to the end user in Kiosk Mode. | - |
| KioskModeManagedFolders | Write | MSFT\_MicrosoftGraphandroiddeviceownerkioskmodemanagedfolder\[\] | A list of managed folders for a device in Kiosk Mode. This collection can contain a maximum of 500 elements. | - |
| KioskModeManagedHomeScreenAutoSignout | Write | Boolean | Whether or not to automatically sign-out of MHS and Shared device mode applications after inactive for Managed Home Screen. | - |
| KioskModeManagedHomeScreenInactiveSignOutDelayInSeconds | Write | UInt32 | Number of seconds to give user notice before automatically signing them out for Managed Home Screen. Valid values 0 to 9999999. | - |
| KioskModeManagedHomeScreenInactiveSignOutNoticeInSeconds | Write | UInt32 | Number of seconds device is inactive before automatically signing user out for Managed Home Screen. Valid values 0 to 9999999. | - |
| KioskModeManagedHomeScreenPinComplexity | Write | String | Complexity of PIN for sign-in session for Managed Home Screen. | `notConfigured`, `simple`, `complex` |
| KioskModeManagedHomeScreenPinRequired | Write | Boolean | Whether or not require user to set a PIN for sign-in session for Managed Home Screen. | - |
| KioskModeManagedHomeScreenPinRequiredToResume | Write | Boolean | Whether or not required user to enter session PIN if screensaver has appeared for Managed Home Screen. | - |
| KioskModeManagedHomeScreenSignInBackground | Write | String | Custom URL background for sign-in screen for Managed Home Screen. | - |
| KioskModeManagedHomeScreenSignInBrandingLogo | Write | String | Custom URL branding logo for sign-in screen and session pin page for Managed Home Screen. | - |
| KioskModeManagedHomeScreenSignInEnabled | Write | Boolean | Whether or not show sign-in screen for Managed Home Screen. | - |
| KioskModeManagedSettingsEntryDisabled | Write | Boolean | Whether or not to use single app kiosk mode or multi-app kiosk mode. | - |
| KioskModeMediaVolumeConfigurationEnabled | Write | Boolean | Whether or not to allow a user to change the media volume in Kiosk Mode. | - |
| KioskModeScreenOrientation | Write | String | Screen orientation configuration for managed home screen in Kiosk Mode. | `notConfigured`, `portrait`, `landscape`, `autoRotate` |
| KioskModeScreenSaverConfigurationEnabled | Write | Boolean | Start screen saver when the device screen times out or locks. | - |
| KioskModeScreenSaverDetectMediaDisabled | Write | Boolean | Whether or not the device screen should show the screen saver if audio/video is playing in Kiosk Mode. | - |
| KioskModeScreenSaverDisplayTimeInSeconds | Write | UInt32 | The number of seconds that the device will display the screen saver for in Kiosk Mode. Valid values 0 to 9999999 | - |
| KioskModeScreenSaverImageUrl | Write | String | URL for an image that will be the device's screen saver in Kiosk Mode. | - |
| KioskModeScreenSaverStartDelayInSeconds | Write | UInt32 | The number of seconds the device needs to be inactive for before the screen saver is shown in Kiosk Mode. Valid values 1 to 9999999 | - |
| KioskModeShowAppNotificationBadge | Write | Boolean | Whether or not to display application notification badges in Kiosk Mode. | - |
| KioskModeShowDeviceInfo | Write | Boolean | Whether or not to allow a user to access basic device information. | - |
| KioskModeUseManagedHomeScreenApp | Write | String | Whether or not to use single app kiosk mode or multi-app kiosk mode. | `notConfigured`, `singleAppMode`, `multiAppMode` |
| KioskModeVirtualHomeButtonEnabled | Write | Boolean | Enable IT administrators to temporarily leave multi-app kiosk mode to make changes on the device. | - |
| KioskModeVirtualHomeButtonType | Write | String | Enable a soft-key button that returns users to the Managed Home Screen. Choose between a persistent, floating button or a button activated by a swipe-up gesture. | `notConfigured`, `swipeUp`, `floating` |
| KioskModeWallpaperUrl | Write | String | Customize the appearance of the screen background for assigned groups. | - |
| KioskModeWifiAllowedSsids | Write | StringArray\[\] | The restricted set of WIFI SSIDs available for the user to configure in Kiosk Mode. This collection can contain a maximum of 500 elements. | - |
| KioskModeWiFiConfigurationEnabled | Write | Boolean | Enable end-users to connect to different Wi-Fi networks. | - |
| MicrophoneForceMute | Write | Boolean | Block unmuting the microphone and adjusting the microphone volume. | - |
| MicrosoftLauncherConfigurationEnabled | Write | Boolean | Indicates whether or not to you want configure Microsoft Launcher. | - |
| MicrosoftLauncherCustomWallpaperAllowUserModification | Write | Boolean | Indicates whether or not the user can modify the wallpaper to personalize their device. | - |
| MicrosoftLauncherCustomWallpaperEnabled | Write | Boolean | Indicates whether or not to configure the wallpaper on the targeted devices. | - |
| MicrosoftLauncherCustomWallpaperImageUrl | Write | String | Indicates the URL for the image file to use as the wallpaper on the targeted devices. | - |
| MicrosoftLauncherDockPresenceAllowUserModification | Write | Boolean | Indicates whether or not the user can modify the device dock configuration on the device. | - |
| MicrosoftLauncherDockPresenceConfiguration | Write | String | Indicates whether or not you want to configure the device dock. | `notConfigured`, `show`, `hide`, `disabled` |
| MicrosoftLauncherFeedAllowUserModification | Write | Boolean | Indicates whether or not the user can modify the launcher feed on the device. | - |
| MicrosoftLauncherFeedEnabled | Write | Boolean | Indicates whether or not the user can modify the launcher feed on the device. | - |
| MicrosoftLauncherSearchBarPlacementConfiguration | Write | String | Indicates whether or not you want to configure the device dock. | `notConfigured`, `top`, `bottom`, `hide` |
| NetworkEscapeHatchAllowed | Write | Boolean | Whether the network escape hatch is enabled. If a network connection can't be made at boot time, the escape hatch prompts the user to temporarily connect to a network in order to refresh the device policy. After applying policy, the temporary network will be forgotten and the device will continue booting. This prevents being unable to connect to a network if there's no suitable network in the last policy and the device boots into an app in lock task mode, or the user is otherwise unable to reach device settings. | - |
| NfcBlockOutgoingBeam | Write | Boolean | Block usage of NFC to beam data from apps. | - |
| PasswordBlockKeyguard | Write | Boolean | Disable lock screen | - |
| PasswordBlockKeyguardFeatures | Write | StringArray\[\] | These features are accessible to users when the device is locked. Users will not be able to see or access disabled features. | `notConfigured`, `camera`, `notifications`, `unredactedNotifications`, `trustAgents`, `fingerprint`, `remoteInput`, `allFeatures`, `face`, `iris`, `biometrics` |
| PasswordExpirationDays | Write | UInt32 | Number of days until device password must be changed. \(1-365\) | - |
| PasswordMinimumLength | Write | UInt32 | Indicates the minimum length of the password required on the device. Valid values 4 to 16 | - |
| PasswordMinimumLetterCharacters | Write | UInt32 | Indicates the minimum number of letter characters required for device password. Valid values 1 to 16 | - |
| PasswordMinimumLowerCaseCharacters | Write | UInt32 | Indicates the minimum number of lower case characters required for device password. Valid values 1 to 16 | - |
| PasswordMinimumNonLetterCharacters | Write | UInt32 | Indicates the minimum number of non-letter characters required for device password. Valid values 1 to 16 | - |
| PasswordMinimumNumericCharacters | Write | UInt32 | Indicates the minimum number of numeric characters required for device password. Valid values 1 to 16 | - |
| PasswordMinimumSymbolCharacters | Write | UInt32 | Indicates the minimum number of symbol characters required for device password. Valid values 1 to 16 | - |
| PasswordMinimumUpperCaseCharacters | Write | UInt32 | Indicates the minimum number of upper case letter characters required for device password. Valid values 1 to 16 | - |
| PasswordMinutesOfInactivityBeforeScreenTimeout | Write | UInt32 | Maximum time after which the device will lock. Can disable screen lock as well so that it never times out. | - |
| PasswordPreviousPasswordCountToBlock | Write | UInt32 | Enter the number of unique passwords required before a user can reuse an old one. \(1-24\) | - |
| PasswordRequiredType | Write | String | Set the password's complexity requirements. Additional password requirements will become available based on your selection. | `deviceDefault`, `required`, `numeric`, `numericComplex`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `customPassword` |
| PasswordRequireUnlock | Write | String | Indicates the timeout period after which a device must be unlocked using a form of strong authentication. | `deviceDefault`, `daily`, `unkownFutureValue` |
| PasswordSignInFailureCountBeforeFactoryReset | Write | UInt32 | Number of consecutive times an incorrect password can be entered before device is wiped of all data. \(4-11\) | - |
| PersonalProfileAppsAllowInstallFromUnknownSources | Write | Boolean | Indicates whether the user can install apps from unknown sources on the personal profile. | - |
| PersonalProfileCameraBlocked | Write | Boolean | Indicates whether to disable the use of the camera on the personal profile. | - |
| PersonalProfilePersonalApplications | Write | MSFT\_MicrosoftGraphapplistitem\[\] | Policy applied to applications in the personal profile. This collection can contain a maximum of 500 elements. | - |
| PersonalProfilePlayStoreMode | Write | String | Used together with PersonalProfilePersonalApplications to control how apps in the personal profile are allowed or blocked | `notConfigured`, `blockedApps`, `allowedApps` |
| PersonalProfileScreenCaptureBlocked | Write | Boolean | Indicates whether to disable the capability to take screenshots on the personal profile. | - |
| PlayStoreMode | Write | String | Users get access to all apps, except the ones you've required uninstall in Client Apps. If you choose 'Not configured' for this setting, users can only access the apps you've listed as available or required in Client Apps. | `notConfigured`, `allowList`, `blockList` |
| ScreenCaptureBlocked | Write | Boolean | Block screen capture | - |
| SecurityCommonCriteriaModeEnabled | Write | Boolean | Represents the security common criteria mode enabled provided to users when they attempt to modify managed settings on their device. | - |
| SecurityDeveloperSettingsEnabled | Write | Boolean | Indicates whether or not the user is allowed to access developer settings like developer options and safe boot on the device. | - |
| SecurityRequireVerifyApps | Write | Boolean | Enable Google Play Protect to scan apps before and after they're installed. If it detects a threat, it might warn the user to remove the app from the device. Required by default. | - |
| ShortHelpText | Write | MSFT\_MicrosoftGraphandroiddeviceowneruserfacingmessage | Represents the customized short help text provided to users when they attempt to modify managed settings on their device. | - |
| StatusBarBlocked | Write | Boolean | Block access to the status bar, including notifications and quick settings. | - |
| StayOnModes | Write | StringArray\[\] | The battery plugged in modes for which the device stays on. When using this setting, it's recommended to clear the Time to lock screen setting so that the device doesn't lock itself while it stays on. | `notConfigured`, `ac`, `usb`, `wireless` |
| StorageAllowUsb | Write | Boolean | Allow USB storage. | - |
| StorageBlockExternalMedia | Write | Boolean | Block mounting of external media. | - |
| StorageBlockUsbFileTransfer | Write | Boolean | Block transfer of files over USB. | - |
| SystemUpdateFreezePeriods | Write | MSFT\_MicrosoftGraphandroiddeviceownersystemupdatefreezeperiod\[\] | Indicates the annually repeating time periods during which system updates are postponed. This collection can contain a maximum of 500 elements. | - |
| SystemUpdateInstallType | Write | String | When over-the-air updates are available for this device, they will be installed based on this policy.? | `deviceDefault`, `postpone`, `windowed`, `automatic` |
| SystemUpdateWindowEndMinutesAfterMidnight | Write | UInt32 | End of the maintenance window in the device's time zone.? | - |
| SystemUpdateWindowStartMinutesAfterMidnight | Write | UInt32 | Beginning of the maintenance window in the device's time zone.? | - |
| SystemWindowsBlocked | Write | Boolean | Disable window notifications such as toasts, incoming calls, outgoing calls, system alerts, and system errors.? | - |
| UsersBlockAdd | Write | Boolean | Blocks users from adding and signing in to personal accounts while on the device. | - |
| UsersBlockRemove | Write | Boolean | Block removal of users. | - |
| VolumeBlockAdjustment | Write | Boolean | Block changes to volume. | - |
| VpnAlwaysOnLockdownMode | Write | Boolean | Enabling this forces all network traffic through the VPN tunnel. If a connection to the VPN can't be established, no network traffic will be allowed. | - |
| VpnAlwaysOnPackageIdentifier | Write | String | Android app package name for app that will handle an always-on VPN connection. | - |
| WifiBlockEditConfigurations | Write | Boolean | Block user creation or editing of any Wi-Fi configurations. | - |
| WifiBlockEditPolicyDefinedConfigurations | Write | Boolean | Block changes to Wi-Fi configurations created by the device owner. Users can create their own Wi-Fi configurations. | - |
| WorkProfilePasswordExpirationDays | Write | UInt32 | Indicates the number of days that a work profile password can be set before it expires and a new password will be required. Valid values 1 to 365 | - |
| WorkProfilePasswordMinimumLength | Write | UInt32 | Indicates the minimum length of the work profile password. Valid values 4 to 16 | - |
| WorkProfilePasswordMinimumLetterCharacters | Write | UInt32 | Indicates the minimum number of numeric characters required for the work profile password. Valid values 1 to 16 | - |
| WorkProfilePasswordMinimumLowerCaseCharacters | Write | UInt32 | Indicates the minimum number of non-letter characters required for the work profile password. Valid values 1 to 16 | - |
| WorkProfilePasswordMinimumNonLetterCharacters | Write | UInt32 | Indicates the minimum number of letter characters required for the work profile password. Valid values 1 to 16 | - |
| WorkProfilePasswordMinimumNumericCharacters | Write | UInt32 | Indicates the minimum number of lower-case characters required for the work profile password. Valid values 1 to 16 | - |
| WorkProfilePasswordMinimumSymbolCharacters | Write | UInt32 | Indicates the minimum number of upper-case letter characters required for the work profile password. Valid values 1 to 16 | - |
| WorkProfilePasswordMinimumUpperCaseCharacters | Write | UInt32 | Indicates the minimum number of symbol characters required for the work profile password. Valid values 1 to 16 | - |
| WorkProfilePasswordPreviousPasswordCountToBlock | Write | UInt32 | Indicates the length of the work profile password history, where the user will not be able to enter a new password that is the same as any password in the history. Valid values 0 to 24 | - |
| WorkProfilePasswordRequiredType | Write | String | Indicates the minimum password quality required on the work profile password. | `deviceDefault`, `required`, `numeric`, `numericComplex`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `customPassword` |
| WorkProfilePasswordRequireUnlock | Write | String | Indicates the timeout period after which a work profile must be unlocked using a form of strong authentication. | `deviceDefault`, `daily`, `unkownFutureValue` |
| WorkProfilePasswordSignInFailureCountBeforeFactoryReset | Write | UInt32 | Indicates the number of times a user can enter an incorrect work profile password before the device is wiped. Valid values 4 to 11 | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphapplistitem

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | odatatype of the item. | `#microsoft.graph.appleAppListItem` |
| appId | Write | String | Kiosk mode managed app id | - |
| appStoreUrl | Write | String | Define the app store URL. | - |
| name | Write | String | Define the name of the app. | - |
| publisher | Write | String | Define the publisher of the app. | - |

#### MSFT\_MicrosoftGraphandroiddeviceowneruserfacingmessage

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| defaultMessage | Write | String | The default message displayed if the user's locale doesn't match with any of the localized messages. | - |
| localizedMessages | Write | MSFT\_MicrosoftGraphkeyvaluepair\[\] | The list of <locale, message> pairs. This collection can contain a maximum of 500 elements. | - |

#### MSFT\_MicrosoftGraphkeyvaluepair

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Write | String | Name of the message localizedMessages. | - |
| Value | Write | String | Value of the message localizedMessages. | - |

#### MSFT\_MicrosoftGraphandroiddeviceownerglobalproxy

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | The type of the global proxy. | `#microsoft.graph.androidDeviceOwnerGlobalProxyAutoConfig`, `#microsoft.graph.androidDeviceOwnerGlobalProxyDirect` |
| proxyAutoConfigURL | Write | String | The proxy auto-config URL. | - |
| excludedHosts | Write | StringArray\[\] | The excluded hosts. | - |
| host | Write | String | The host name. | - |
| port | Write | UInt32 | The port. | - |

#### MSFT\_MicrosoftGraphandroiddeviceownerkioskmodeapppositionitem

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| item | Write | MSFT\_MicrosoftGraphandroiddeviceownerkioskmodehomescreenitem | Item to be arranged. | - |
| position | Write | UInt32 | Position of the item on the grid. Valid values 0 to 9999999. | - |

#### MSFT\_MicrosoftGraphandroiddeviceownerkioskmodehomescreenitem

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | Type of the item. | `#microsoft.graph.androidDeviceOwnerKioskModeApp`, `#microsoft.graph.androidDeviceOwnerKioskModeWeblink`, `#microsoft.graph.androidDeviceOwnerKioskModeManagedFolder` |
| folderIdentifier | Write | String | The folder identifier. | - |
| folderName | Write | String | The folder name. | - |
| items | Write | MSFT\_MicrosoftGraphandroiddeviceownerkioskmodefolderitem\[\] | Item to be arranged. | - |
| className | Write | String | The class name of the item. | - |
| package | Write | String | The package of the item. | - |
| label | Write | String | The label of the item. | - |
| link | Write | String | The link of the item. | - |

#### MSFT\_MicrosoftGraphandroiddeviceownerkioskmodemanagedfolder

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| folderIdentifier | Write | String | The folder identifier. | - |
| folderName | Write | String | The folder name. | - |
| items | Write | MSFT\_MicrosoftGraphandroiddeviceownerkioskmodefolderitem\[\] | Item to be arranged. | - |

#### MSFT\_MicrosoftGraphandroiddeviceownerkioskmodefolderitem

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | The type of the item. | `#microsoft.graph.androidDeviceOwnerKioskModeApp`, `#microsoft.graph.androidDeviceOwnerKioskModeWeblink` |
| className | Write | String | The class name of the item. | - |
| package | Write | String | The package of the item. | - |
| label | Write | String | The label of the item. | - |
| link | Write | String | The link of the item. | - |

#### MSFT\_MicrosoftGraphandroiddeviceownersystemupdatefreezeperiod

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| endDay | Write | UInt32 | The day of the end date of the freeze period. Valid values 1 to 31. | - |
| endMonth | Write | UInt32 | The month of the end date of the freeze period. Valid values 1 to 12. | - |
| startDay | Write | UInt32 | The day of the start date of the freeze period. Valid values 1 to 31. | - |
| startMonth | Write | UInt32 | The month of the start date of the freeze period. Valid values 1 to 12. | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationPolicyAndroidOpenSourceProject resource type

### Description

This resource configures an Intune device configuration profile for an Android Open Source Project Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune policy. | - |
| DisplayName | Key | String | Display name of the Intune policy. | - |
| Description | Write | String | Description of the Intune policy. | - |
| AppsBlockInstallFromUnknownSources | Write | Boolean | Prevent applications from unknown sources. | - |
| BluetoothBlockConfiguration | Write | Boolean | Prevent bluetooth configuration. | - |
| BluetoothBlocked | Write | Boolean | Prevents using Bluetooth on devices. | - |
| CameraBlocked | Write | Boolean | Prevents access to the device camera. | - |
| FactoryResetBlocked | Write | Boolean | Prevent factory reset. | - |
| PasswordMinimumLength | Write | UInt32 | Minimum number of characters required for the password. | - |
| PasswordMinutesOfInactivityBeforeScreenTimeout | Write | UInt32 | Maximum minutes of inactivity until screen locks. | - |
| PasswordRequiredType | Write | String | Set password complexity. | `deviceDefault`, `required`, `numeric`, `numericComplex`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `customPassword` |
| PasswordSignInFailureCountBeforeFactoryReset | Write | UInt32 | Number of sign-in failures before wiping device. | - |
| ScreenCaptureBlocked | Write | Boolean | Prevent screen capture. | - |
| SecurityAllowDebuggingFeatures | Write | Boolean | Enable debugging features. | - |
| StorageBlockExternalMedia | Write | Boolean | Prevent external media. | - |
| StorageBlockUsbFileTransfer | Write | Boolean | Prevent USB file transfer. | - |
| WifiBlockEditConfigurations | Write | Boolean | Prevent Wifi configuration edit. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationPolicyAndroidWorkProfile resource type

### Description

This resource configures an Intune device configuration profile for an Android WorkProfile Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the device general configuration policy for Android WorkProfile. | - |
| Description | Write | String | Description of the device general configuration policy for Android WorkProfile | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the Intune Policy. | - |
| PasswordBlockFaceUnlock | Write | Boolean | Indicates whether or not to block face unlock. | - |
| PasswordBlockFingerprintUnlock | Write | Boolean | Indicates whether or not to block fingerprint unlock | - |
| PasswordBlockIrisUnlock | Write | Boolean | Indicates whether or not to block iris unlock. | - |
| passwordBlockTrustAgents | Write | Boolean | Indicates whether or not to block Smart Lock and other trust agents. | - |
| PasswordExpirationDays | Write | UInt32 | Number of days before the password expires | - |
| PasswordMinimumLength | Write | UInt32 | Minimum length of passwords | - |
| PasswordMinutesOfInactivityBeforeScreenTimeout | Write | UInt32 | Minutes of inactivity before the screen times out | - |
| PasswordPreviousPasswordBlockCount | Write | UInt32 | Number of previous passwords to block | - |
| PasswordSignInFailureCountBeforeFactoryReset | Write | UInt32 | Number of sign in failures allowed before factory reset | - |
| PasswordRequiredType | Write | String | Type of password that is required | `deviceDefault`, `lowSecurityBiometric`, `required`, `atLeastNumeric`, `numericComplex`, `atLeastAlphabetic`, `atLeastAlphanumeric`, `alphanumericWithSymbols` |
| RequiredPasswordComplexity | Write | String | Indicates the required device password complexity on Android. One of: NONE, LOW, MEDIUM, HIGH. | `none`, `low`, `medium`, `high` |
| WorkProfileAllowAppInstallsFromUnknownSources | Write | Boolean | Indicates whether to allow installation of apps from unknown sources. | - |
| WorkProfileDataSharingType | Write | String | Type of data sharing that is allowed | `deviceDefault`, `preventAny`, `allowPersonalToWork`, `noRestrictions` |
| WorkProfileBlockNotificationsWhileDeviceLocked | Write | Boolean | Indicates whether or not to block notifications while device locked | - |
| WorkProfileBlockAddingAccounts | Write | Boolean | Block users from adding/removing accounts in work profile | - |
| WorkProfileBluetoothEnableContactSharing | Write | Boolean | Allow bluetooth devices to access enterprise contacts | - |
| WorkProfileBlockScreenCapture | Write | Boolean | Block screen capture in work profile | - |
| WorkProfileBlockCrossProfileCallerId | Write | Boolean | Block display work profile caller ID in personal profile | - |
| WorkProfileBlockCamera | Write | Boolean | Block work profile camera | - |
| WorkProfileBlockCrossProfileContactsSearch | Write | Boolean | Block work profile contacts availability in personal profile | - |
| WorkProfileBlockCrossProfileCopyPaste | Write | Boolean | Boolean that indicates if the setting disallow cross profile copy paste is enabled | - |
| WorkProfileDefaultAppPermissionPolicy | Write | String | Type of password that is required | `deviceDefault`, `prompt`, `autoGrant`, `autoDeny` |
| WorkProfilePasswordBlockFaceUnlock | Write | Boolean | Indicates whether or not to block face unlock in work profile. | - |
| WorkProfilePasswordBlockFingerprintUnlock | Write | Boolean | Indicates whether or not to block fingerprint unlock in work profile | - |
| WorkProfilePasswordBlockIrisUnlock | Write | Boolean | Indicates whether or not to block iris unlock in work profile. | - |
| WorkProfilePasswordBlockTrustAgents | Write | Boolean | Indicates whether or not to block Smart Lock and other trust agents for work profile | - |
| WorkProfilePasswordExpirationDays | Write | UInt32 | Number of days before the work profile password expires | - |
| WorkProfilePasswordMinimumLength | Write | UInt32 | Minimum length of work profile password | - |
| WorkProfilePasswordMinNumericCharacters | Write | UInt32 | Minimum count of numeric characters required in work profile password | - |
| WorkProfilePasswordMinNonLetterCharacters | Write | UInt32 | Minimum count of non-letter characters required in work profile password | - |
| WorkProfilePasswordMinLetterCharacters | Write | UInt32 | Minimum count of letter characters required in work profile password | - |
| WorkProfilePasswordMinLowerCaseCharacters | Write | UInt32 | Minimum count of lower-case characters required in work profile password | - |
| WorkProfilePasswordMinUpperCaseCharacters | Write | UInt32 | Minimum count of upper-case characters required in work profile password | - |
| WorkProfilePasswordMinSymbolCharacters | Write | UInt32 | Minimum count of symbols required in work profile password | - |
| WorkProfilePasswordMinutesOfInactivityBeforeScreenTimeout | Write | UInt32 | Minutes of inactivity before the screen times out | - |
| WorkProfilePasswordPreviousPasswordBlockCount | Write | UInt32 | Number of previous work profile passwords to block | - |
| WorkProfilePasswordSignInFailureCountBeforeFactoryReset | Write | UInt32 | Number of sign in failures allowed before work profile is removed and all corporate data deleted | - |
| WorkProfilePasswordRequiredType | Write | String | Type of work profile password that is required | `deviceDefault`, `lowSecurityBiometric`, `required`, `atLeastNumeric`, `numericComplex`, `atLeastAlphabetic`, `atLeastAlphanumeric`, `alphanumericWithSymbols` |
| WorkProfileRequiredPasswordComplexity | Write | String | Indicates the required device password complexity on Android. One of: NONE, LOW, MEDIUM, HIGH in work profile. | `none`, `low`, `medium`, `high` |
| WorkProfileRequirePassword | Write | Boolean | Password is required or not for work profile | - |
| SecurityRequireVerifyApps | Write | Boolean | Require the Android Verify apps feature is turned on | - |
| VpnAlwaysOnPackageIdentifier | Write | String | Package identifier for always-on VPN. | - |
| VpnEnableAlwaysOnLockdownMode | Write | Boolean | Enable lockdown mode for always-on VPN. | - |
| WorkProfileAllowWidgets | Write | Boolean | Allow widgets from work profile apps. | - |
| WorkProfileBlockPersonalAppInstallsFromUnknownSources | Write | Boolean | Prevent app installations from unknown sources in the personal profile. | - |
| Ensure | Write | String | Present ensures the site collection exists, absent ensures it's removed | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationPolicyiOS resource type

### Description

This resource configures an Intune Device Configuration Policy for iOS.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune policy. | - |
| DisplayName | Key | String | Display name of the Intune policy. | - |
| Description | Write | String | Description of the Intune policy. | - |
| AccountBlockModification | Write | Boolean | Indicates whether or not to allow account modification when the device is in supervised mode. | - |
| ActivationLockAllowWhenSupervised | Write | Boolean | Activation Lock makes it harder for a lost or stolen device to be reactivated. | - |
| AirDropBlocked | Write | Boolean | Indicates whether or not to allow AirDrop when the device is in supervised mode. | - |
| AirDropForceUnmanagedDropTarget | Write | Boolean | Force AirDrop to be considered an unmanaged drop target. | - |
| AirPlayForcePairingPasswordForOutgoingRequests | Write | Boolean | Force requiring a pairing password for outgoing AirPlay requests. | - |
| AirPrintBlockCredentialsStorage | Write | Boolean | Blocks keychain storage of username and password for outgoing AirPrint request. | - |
| AirPrintBlocked | Write | Boolean | Blocks AirPrint request. | - |
| AirPrintBlockiBeaconDiscovery | Write | Boolean | Blocking prevents malicious AirPrint Bluetooth beacons phishing for network traffic. | - |
| AirPrintForceTrustedTLS | Write | Boolean | Forces trusted certificates for TLS printing communication | - |
| AppClipsBlocked | Write | Boolean | Block app clips. | - |
| AppleNewsBlocked | Write | Boolean | Block Apple News | - |
| ApplePersonalizedAdsBlocked | Write | Boolean | Block Apple PersonalizedAdsBlocked | - |
| AppleWatchBlockPairing | Write | Boolean | Indicates whether or not to allow Apple Watch pairing when the device is in supervised mode \(iOS 9.0 and later\). | - |
| AppleWatchForceWristDetection | Write | Boolean | Force paired Apple watch to use wrist detection. | - |
| AppRemovalBlocked | Write | Boolean | Block app removal. | - |
| AppsSingleAppModeList | Write | MSFT\_MicrosoftGraphapplistitem\[\] | Apps you add to this list and assign to a device can lock the device to run only that app once launched, or lock the device while a certain action is running \(for example, taking a test\). Once the action is complete, or you remove the restriction, the device returns to its normal state. | - |
| AppStoreBlockAutomaticDownloads | Write | Boolean | Blocks automatic downloading of apps purchased on other devices. Does not affect updates to existing apps. | - |
| AppStoreBlocked | Write | Boolean | For supervised devices as of iOS 13.0. | - |
| AppStoreBlockInAppPurchases | Write | Boolean | Block AppStore in-app purchases. | - |
| AppStoreBlockUIAppInstallation | Write | Boolean | Block App Store from Home Screen. Users may continue to use iTunes or Apple Configurator to install or update apps. | - |
| AppStoreRequirePassword | Write | Boolean | Users must enter Apple ID password for each in-app and iTunes purchase. | - |
| AppsVisibilityList | Write | MSFT\_MicrosoftGraphapplistitem\[\] | Enter the iTunes App Store URL of the app you want. For example, to specify the Microsoft Work Folders app for iOS, enter [https://itunes.apple.com/us/app/work-folders/id950878067?mt=8](https://itunes.apple.com/us/app/work-folders/id950878067?mt=8). To find the URL of an app, use a search engine to locate the store page. For example, to find the Work Folders app, you could search Microsoft Work Folders ITunes. | - |
| AppsVisibilityListType | Write | String | Set whether the list is a list of apps to hide or a list of apps to make visible. | `none`, `appsInListCompliant`, `appsNotInListCompliant` |
| AutoFillForceAuthentication | Write | Boolean | Require Touch ID or Face ID before passwords or credit card information can be auto filled in Safari and Apps. Available with iOS 12.0 and later. | - |
| AutoUnlockBlocked | Write | Boolean | Block auto unlock. | - |
| BlockSystemAppRemoval | Write | Boolean | Blocking disables the ability to remove system apps from the device. | - |
| BluetoothBlockModification | Write | Boolean | Block modification of Bluetooth settings. To use this setting, the device must be in supervised mode \(iOS 10.0+\). | - |
| CameraBlocked | Write | Boolean | Indicates whether or not to block the user from accessing the camera of the device. Requires a supervised device for iOS 13 and later. | - |
| CellularBlockDataRoaming | Write | Boolean | Block data roaming over the cellular network. This won't show in the device's management profile, but a block will be enforced for data roaming every time the device checks in \(typically every 8 hours\). | - |
| CellularBlockGlobalBackgroundFetchWhileRoaming | Write | Boolean | Block global background fetch while roaming over the cellular network. | - |
| CellularBlockPerAppDataModification | Write | Boolean | Block changes to app cellular data usage settings. | - |
| CellularBlockPersonalHotspot | Write | Boolean | This value is available only with certain carriers. This won't show in the device's management profile, but a block will be enforced for personal hotspot every time the device checks in \(typically every 8 hours\). Block modification of personal hotspot in addition to this setting to ensure personal hotspot will always be blocked. | - |
| CellularBlockPersonalHotspotModification | Write | Boolean | For devices running iOS 12.2 and later. Users can't turn Personal Hotspot on or off. If you block this setting and block Personal Hotspot, Personal Hotspot will be turned off. | - |
| CellularBlockPlanModification | Write | Boolean | Indicates whether or not to allow users to change the settings of the cellular plan on a supervised device. | - |
| CellularBlockVoiceRoaming | Write | Boolean | Block voice roaming over the cellular network. | - |
| CertificatesBlockUntrustedTlsCertificates | Write | Boolean | Block untrusted Transport Layer Security \(TLS\) certificates. | - |
| ClassroomAppBlockRemoteScreenObservation | Write | Boolean | Block remote screen observation by Classroom app. To use this setting, the device must be in supervised mode \(iOS 9.3+\). | - |
| ClassroomAppForceUnpromptedScreenObservation | Write | Boolean | Student devices enrolled in a class via the Classroom app will automatically give permission to that course's teacher to silently observe the student's screen. | - |
| ClassroomForceAutomaticallyJoinClasses | Write | Boolean | Students can join a class without prompting the teacher. | - |
| ClassroomForceRequestPermissionToLeaveClasses | Write | Boolean | Requires a student enrolled in an unmanaged course via Classroom to request permission from the teacher when attempting to leave the course. Only available in iOS 11.3+ | - |
| ClassroomForceUnpromptedAppAndDeviceLock | Write | Boolean | Teachers can lock an app open or lock the device without first prompting the user. | - |
| CompliantAppListType | Write | String | Device compliance can be viewed in the Restricted Apps Compliance report. | `none`, `appsInListCompliant`, `appsNotInListCompliant` |
| CompliantAppsList | Write | MSFT\_MicrosoftGraphapplistitem\[\] | Enter the iTunes App Store URL of the app you want. For example, to specify the Microsoft Work Folders app for iOS, enter [https://itunes.apple.com/us/app/work-folders/id950878067?mt=8](https://itunes.apple.com/us/app/work-folders/id950878067?mt=8). To find the URL of an app, use a search engine to locate the store page. For example, to find the Work Folders app, you could search Microsoft Work Folders ITunes. | - |
| ConfigurationProfileBlockChanges | Write | Boolean | Indicates whether or not to block the user from installing configuration profiles and certificates interactively when the device is in supervised mode. | - |
| ContactsAllowManagedToUnmanagedWrite | Write | Boolean | Users can sync and add their managed contacts \(including business and corporate ones\) to an unmanaged app, such as the device's built-in contacts app. | - |
| ContactsAllowUnmanagedToManagedRead | Write | Boolean | An unmanaged app, such as the device's built-in contacts app, can access contact info in a managed app, such as Outlook. | - |
| ContinuousPathKeyboardBlocked | Write | Boolean | QuickPath enables continuous input on the device keyboard. Available for iOS/iPadOS 13.0 and later. | - |
| DateAndTimeForceSetAutomatically | Write | Boolean | Forces device to Set Date & Time Automatically. The device's time zone will only be updated when the device has cellular connections or wifi with location services enabled. | - |
| DefinitionLookupBlocked | Write | Boolean | Indicates whether or not to block definition lookup when the device is in supervised mode \(iOS 8.1.3 and later \). | - |
| DeviceBlockEnableRestrictions | Write | Boolean | On iOS 12.0 and later, this blocks users from setting their own Screen Time settings, which includes device restrictions. On iOS 11.4.1 and earlier, this blocks the user from enabling restrictions in the device settings. The blocking effect is the same on any supervised iOS device. | - |
| DeviceBlockEraseContentAndSettings | Write | Boolean | Block the use of the erase all content and settings option on the device. | - |
| DeviceBlockNameModification | Write | Boolean | Indicates whether or not to allow device name modification when the device is in supervised mode \(iOS 9.0 and later\). | - |
| DiagnosticDataBlockSubmission | Write | Boolean | Block the device from sending diagnostic and usage telemetry data. | - |
| DiagnosticDataBlockSubmissionModification | Write | Boolean | Block the modification of the diagnostic submission and app analytics settings in the Diagnostics and Usage pane in Settings. To use this setting, the device must be in supervised mode \(iOS 9.3.2+\). | - |
| DocumentsBlockManagedDocumentsInUnmanagedApps | Write | Boolean | Indicates whether or not to block the user from viewing managed documents in unmanaged apps. | - |
| DocumentsBlockUnmanagedDocumentsInManagedApps | Write | Boolean | Indicates whether or not to block the user from viewing unmanaged documents in managed apps. | - |
| EmailInDomainSuffixes | Write | StringArray\[\] | Emails that the user sends or receives which don't match the domains you specify here will be marked as untrusted. | - |
| EnterpriseAppBlockTrust | Write | Boolean | Removes the Trust Enterprise Developer button in Settings->General->Profiles & Device Management. | - |
| EnterpriseAppBlockTrustModification | Write | Boolean | Block the changing of enterprise app trust settings. | - |
| EnterpriseBookBlockBackup | Write | Boolean | Indicates whether or not to backup enterprise book. | - |
| EnterpriseBookBlockMetadataSync | Write | Boolean | Indicates whether or not to sync enterprise book metadata. | - |
| EsimBlockModification | Write | Boolean | Indicates whether or not to allow the addition or removal of cellular plans on the eSIM of a supervised device. | - |
| FaceTimeBlocked | Write | Boolean | Indicates whether or not to block the user from using FaceTime. Requires a supervised device for iOS 13 and later. | - |
| FilesNetworkDriveAccessBlocked | Write | Boolean | Using the Server Message Block \(SMB\) protocol, devices can access files or other resources on a network server. Available for devices running iOS and iPadOS, versions 13.0 and later. | - |
| FilesUsbDriveAccessBlocked | Write | Boolean | Devices with access can connect to and open files on a USB drive. Available for devices running iOS and iPadOS, versions 13.0 and later. | - |
| FindMyDeviceInFindMyAppBlocked | Write | Boolean | A Find My app feature. Available for iOS/iPadOS 13.0 and later. | - |
| FindMyFriendsBlocked | Write | Boolean | Block changes to the Find My Friends app settings. | - |
| FindMyFriendsInFindMyAppBlocked | Write | Boolean | A Find My app feature. Used to locate family and friends from an Apple device or iCloud.com. Available for iOS/iPadOS 13.0 and later. | - |
| GameCenterBlocked | Write | Boolean | Indicates whether or not to block the user from using Game Center when the device is in supervised mode. | - |
| GamingBlockGameCenterFriends | Write | Boolean | Block adding Game Center friends. For supervised devices as of iOS 13.0. | - |
| GamingBlockMultiplayer | Write | Boolean | For supervised devices as of iOS 13.0. | - |
| HostPairingBlocked | Write | Boolean | Host pairing allows you to control which devices the device can pair with. | - |
| IBooksStoreBlocked | Write | Boolean | Indicates whether or not to block the user from using the iBooks Store when the device is in supervised mode. | - |
| IBooksStoreBlockErotica | Write | Boolean | User will not be able to download media from the iBook store that has been tagged as erotica. | - |
| ICloudBlockActivityContinuation | Write | Boolean | Handoff lets users start work on one iOS device, and continue it on another MacOS or iOS device. | - |
| ICloudBlockBackup | Write | Boolean | Block backing up device to iCloud. | - |
| ICloudBlockDocumentSync | Write | Boolean | Blocks iCloud from syncing documents and data. | - |
| ICloudBlockManagedAppsSync | Write | Boolean | Block managed apps from syncing to cloud. | - |
| ICloudBlockPhotoLibrary | Write | Boolean | Any photos not fully downloaded from iCloud Photo Library to device will be removed from local storage. | - |
| ICloudBlockPhotoStreamSync | Write | Boolean | Block photo stream syncing to iCloud. | - |
| ICloudBlockSharedPhotoStream | Write | Boolean | Block shared photo streaming. Blocking can cause data loss. | - |
| ICloudPrivateRelayBlocked | Write | Boolean | Block iCloud private relay. | - |
| ICloudRequireEncryptedBackup | Write | Boolean | Require encryption on device backup. | - |
| ITunesBlocked | Write | Boolean | Block iTunes. | - |
| ITunesBlockExplicitContent | Write | Boolean | Block explicit iTunes music, podcast, and news content from iTunes. For supervised devices as of 13.0. | - |
| ITunesBlockMusicService | Write | Boolean | Block Music service. If true, Music app reverts to classic mode and Music service is disabled. | - |
| ITunesBlockRadio | Write | Boolean | Indicates whether or not to block the user from using iTunes Radio when the device is in supervised mode \(iOS 9.3 and later\). | - |
| KeyboardBlockAutoCorrect | Write | Boolean | Indicates whether or not to block keyboard auto-correction when the device is in supervised mode \(iOS 8.1.3 and later\). | - |
| KeyboardBlockDictation | Write | Boolean | Indicates whether or not to block the user from using dictation input when the device is in supervised mode. | - |
| KeyboardBlockPredictive | Write | Boolean | Indicates whether or not to block predictive keyboards when device is in supervised mode \(iOS 8.1.3 and later\). | - |
| KeyboardBlockShortcuts | Write | Boolean | Indicates whether or not to block keyboard shortcuts when the device is in supervised mode \(iOS 9.0 and later\). | - |
| KeyboardBlockSpellCheck | Write | Boolean | Indicates whether or not to block keyboard spell-checking when the device is in supervised mode \(iOS 8.1.3 and later\). | - |
| KeychainBlockCloudSync | Write | Boolean | Disables syncing credentials stored in the Keychain to iCloud. | - |
| KioskModeAllowAssistiveSpeak | Write | Boolean | Indicates whether or not to allow assistive speak while in kiosk mode. | - |
| KioskModeAllowAssistiveTouchSettings | Write | Boolean | Users can turn AssistiveTouch on or off. | - |
| KioskModeAllowAutoLock | Write | Boolean | Kiosk mode allow auto lock | - |
| KioskModeAllowColorInversionSettings | Write | Boolean | Users can turn invert colors on or off. | - |
| KioskModeAllowRingerSwitch | Write | Boolean | Kiosk mode allow ringer switch | - |
| KioskModeAllowScreenRotation | Write | Boolean | Kiosk mode allow screen rotation | - |
| KioskModeAllowSleepButton | Write | Boolean | Kiosk mode allow sleep button | - |
| KioskModeAllowTouchscreen | Write | Boolean | Kiosk mode allow touchscreen | - |
| KioskModeAllowVoiceControlModification | Write | Boolean | Indicates whether or not to allow the user to toggle voice control in kiosk mode. | - |
| KioskModeAllowVoiceOverSettings | Write | Boolean | Users can turn VoiceOver on or off. | - |
| KioskModeAllowVolumeButtons | Write | Boolean | Kiosk mode allow volume buttons | - |
| KioskModeAllowZoomSettings | Write | Boolean | Users can turn zoom on or off. | - |
| KioskModeAppStoreUrl | Write | String | URL of app for kiosk mode, e.g. [https://itunes.apple.com/us/app/work-folders/id950878067?mt=8](https://itunes.apple.com/us/app/work-folders/id950878067?mt=8) | - |
| KioskModeAppType | Write | String | Indicates type of app in kiosk mode. | `notConfigured`, `appStoreApp`, `managedApp`, `builtInApp` |
| KioskModeBlockAutoLock | Write | Boolean | Indicates whether or not to block the auto-lock while in Kiosk Mode. | - |
| KioskModeBlockRingerSwitch | Write | Boolean | Indicates whether or not to block the ringer switch while in Kiosk Mode. | - |
| KioskModeBlockScreenRotation | Write | Boolean | Indicates whether or not to block the screen rotation while in Kiosk Mode. | - |
| KioskModeBlockSleepButton | Write | Boolean | Indicates whether or not to block the sleep button while in Kiosk Mode. | - |
| KioskModeBlockTouchscreen | Write | Boolean | Indicates whether or not to block the touchscreen while in Kiosk Mode. | - |
| KioskModeBlockVolumeButtons | Write | Boolean | Indicates whether or not to block the volume buttons while in Kiosk Mode. | - |
| KioskModeBuiltInAppId | Write | String | To see a list of bundle IDs for common built-in iOS apps, see the Intune documentation. | - |
| KioskModeEnableVoiceControl | Write | Boolean | Indicates whether or not to enable the voice control while in Kiosk Mode. | - |
| KioskModeManagedAppId | Write | String | Add managed Intune apps from the Software Node. | - |
| KioskModeRequireAssistiveTouch | Write | Boolean | Indicates whether or not to enforce assistive touch while in Kiosk Mode. | - |
| KioskModeRequireColorInversion | Write | Boolean | Indicates whether or not to enforce color inversion while in Kiosk Mode. | - |
| KioskModeRequireMonoAudio | Write | Boolean | Indicates whether or not to enforce mono audio while in Kiosk Mode. | - |
| KioskModeRequireVoiceOver | Write | Boolean | Indicates whether or not to enforce voice control while in Kiosk Mode. | - |
| KioskModeRequireZoom | Write | Boolean | Indicates whether or not to enforce zoom while in Kiosk Mode. | - |
| LockScreenBlockControlCenter | Write | Boolean | Indicates whether or not to block the user from using control center on the lock screen. | - |
| LockScreenBlockNotificationView | Write | Boolean | Indicates whether or not to block the user from using the notification view on the lock screen. | - |
| LockScreenBlockPassbook | Write | Boolean | Indicates whether or not to block the user from using passbook when the device is locked. | - |
| LockScreenBlockTodayView | Write | Boolean | Indicates whether or not to block the user from using the Today View on the lock screen. | - |
| ManagedPasteboardRequired | Write | Boolean | Indicates whether or not to enforce managed pasteboard. | - |
| MediaContentRatingApps | Write | String | Media content rating settings for apps. | `allAllowed`, `allBlocked`, `agesAbove4`, `agesAbove9`, `agesAbove12`, `agesAbove17` |
| MediaContentRatingAustralia | Write | MSFT\_MicrosoftGraphmediacontentratingaustralia | Media content rating settings for Australia | - |
| MediaContentRatingCanada | Write | MSFT\_MicrosoftGraphmediacontentratingcanada | Media content rating settings for Canada | - |
| MediaContentRatingFrance | Write | MSFT\_MicrosoftGraphmediacontentratingfrance | Media content rating settings for France | - |
| MediaContentRatingGermany | Write | MSFT\_MicrosoftGraphmediacontentratinggermany | Media content rating settings for Germany | - |
| MediaContentRatingIreland | Write | MSFT\_MicrosoftGraphmediacontentratingireland | Media content rating settings for Ireland | - |
| MediaContentRatingJapan | Write | MSFT\_MicrosoftGraphmediacontentratingjapan | Media content rating settings for Japan | - |
| MediaContentRatingNewZealand | Write | MSFT\_MicrosoftGraphmediacontentratingnewzealand | Media content rating settings for New Zealand | - |
| MediaContentRatingUnitedKingdom | Write | MSFT\_MicrosoftGraphmediacontentratingunitedkingdom | Media content rating settings for United Kingdom | - |
| MediaContentRatingUnitedStates | Write | MSFT\_MicrosoftGraphmediacontentratingunitedstates | Media content rating settings for United States | - |
| MessagesBlocked | Write | Boolean | Indicates whether or not to block the user from using the Messages app on the supervised device. | - |
| NetworkUsageRules | Write | MSFT\_MicrosoftGraphiosnetworkusagerule\[\] | If you don't add any managed apps, the configured settings will apply to all managed apps by default. If you add specific managed apps, the configured settings will apply to only those apps. | - |
| NfcBlocked | Write | Boolean | Indicates whether or not to block the user from using nfc on the supervised device. | - |
| NotificationsBlockSettingsModification | Write | Boolean | Indicates whether or not to allow notifications settings modification \(iOS 9.3 and later\). | - |
| OnDeviceOnlyDictationForced | Write | Boolean | Indicates whether or not to enforce on device only dictation. | - |
| OnDeviceOnlyTranslationForced | Write | Boolean | Indicates whether or not to enforce on device only translation. | - |
| PasscodeBlockFingerprintModification | Write | Boolean | Block users from adding, changing, or removing fingerprints and faces. Face ID is avaliable in iOS 11.0 and later. | - |
| PasscodeBlockFingerprintUnlock | Write | Boolean | Face ID is avaliable on iOS 11.0 and later. | - |
| PasscodeBlockModification | Write | Boolean | Block passcode from being added, changed or removed. Changes to passcode restrictions will be ignored on supervised devices after blocking passcode modification. | - |
| PasscodeBlockSimple | Write | Boolean | Block simple password sequences, such as 1234 or 1111. | - |
| PasscodeExpirationDays | Write | UInt32 | Number of days until device password must be changed. \(1-65535\) | - |
| PasscodeMinimumCharacterSetCount | Write | UInt32 | Minimum number \(0-4\) of non-alphanumeric characters, such as #, %, !, etc., required in the password. The default value is 0. | - |
| PasscodeMinimumLength | Write | UInt32 | Minimum number of digits or characters in password. \(4-14\) | - |
| PasscodeMinutesOfInactivityBeforeLock | Write | UInt32 | Set to 0 to require a password immediately. there's no maximum number of minutes, and this number overrides the number currently set on the device. \(This compliance check is supported for devices with OS versions iOS 8.0 and above\) | - |
| PasscodeMinutesOfInactivityBeforeScreenTimeout | Write | UInt32 | Set to 0 to use the device's minimum possible value. This number \(0-60\) overrides the number currently set on the device. If set to Immediately, devices will use the minimum possible value per device. | - |
| PasscodePreviousPasscodeBlockCount | Write | UInt32 | Number of new passwords that must be used until an old one can be reused. \(1-24\) | - |
| PasscodeRequired | Write | Boolean | In addition to requiring a password on all devices, this setting enforces a non-simple, 6-digit password requirement \(regardless of other password settings you configure\) on devices that are enrolled with Apple user enrollment. | - |
| PasscodeRequiredType | Write | String | Type of passcode that is required. | `deviceDefault`, `alphanumeric`, `numeric` |
| PasscodeSignInFailureCountBeforeWipe | Write | UInt32 | Number of consecutive times an incorrect password can be entered before device is wiped of all data. \(2-11\) | - |
| PasswordBlockAirDropSharing | Write | Boolean | Indicates whether or not to block AirDrop password sharing | - |
| PasswordBlockAutoFill | Write | Boolean | Indicates whether or not to block password autofill. | - |
| PasswordBlockProximityRequests | Write | Boolean | Indicates whether or not to block password proximity requests. | - |
| PkiBlockOTAUpdates | Write | Boolean | Allows your users to receive software updates without connecting their devices to a computer | - |
| PodcastsBlocked | Write | Boolean | Indicates whether or not to block podcasts. | - |
| PrivacyForceLimitAdTracking | Write | Boolean | Disables device advertising identifier | - |
| ProximityBlockSetupToNewDevice | Write | Boolean | Block user's from using their Apple devices to set up and configure other Apple devices. | - |
| SafariBlockAutofill | Write | Boolean | Indicates whether or not to block Safari autofill. | - |
| SafariBlocked | Write | Boolean | Indicates whether or not to block Safari. For supervised devices as of iOS 13.0. | - |
| SafariBlockJavaScript | Write | Boolean | Indicates whether or not to block javascript in Safari. | - |
| SafariBlockPopups | Write | Boolean | Indicates whether or not to block popups on Safari. | - |
| SafariCookieSettings | Write | String | Cookie settings for Safari. | `browserDefault`, `blockAlways`, `allowCurrentWebSite`, `allowFromWebsitesVisited`, `allowAlways` |
| SafariManagedDomains | Write | StringArray\[\] | Documents downloaded from the URLs you specify here will be considered managed \(Safari only\). | - |
| SafariPasswordAutoFillDomains | Write | StringArray\[\] | Users can save passwords in Safari only from URLs matching the patterns you specify here. To use this setting, the device must be in supervised mode and not configured for multiple users. \(iOS 9.3+\) | - |
| SafariRequireFraudWarning | Write | Boolean | Indicates whether or not to require fraud warning in Safari. | - |
| ScreenCaptureBlocked | Write | Boolean | Indicates whether or not to block the user from taking Screenshots | - |
| SharedDeviceBlockTemporarySessions | Write | Boolean | Indicates whether or not to block temporary sessions on shared devices. | - |
| SiriBlocked | Write | Boolean | Indicates whether or not to block Siri. | - |
| SiriBlockedWhenLocked | Write | Boolean | Indicates whether or not to block Siri when locked. | - |
| SiriBlockUserGeneratedContent | Write | Boolean | Block Siri from querying user-generated content from the internet. | - |
| SiriRequireProfanityFilter | Write | Boolean | Prevents Siri from dictating, or speaking profane language. | - |
| SoftwareUpdatesEnforcedDelayInDays | Write | UInt32 | Delay the user's software update for this many days. The maximum is 90 days. \(1-90\) | - |
| SoftwareUpdatesForceDelayed | Write | Boolean | Delay user visibility of Software Updates. This does not impact any scheduled updates. It represents days before software updates are visible to end users after release. | - |
| SpotlightBlockInternetResults | Write | Boolean | Blocks Spotlight from returning any results from an Internet search. | - |
| UnpairedExternalBootToRecoveryAllowed | Write | Boolean | Allow users to boot devices into recovery mode with unpaired devices. Available for devices running iOS and iPadOS versions 14.5 and later. | - |
| UsbRestrictedModeBlocked | Write | Boolean | Blocks USB Restricted mode. USB Restricted mode blocks USB accessories from exchanging data with a device that has been locked over an hour. | - |
| VoiceDialingBlocked | Write | Boolean | Indicates whether or not to block voice dialing. | - |
| VpnBlockCreation | Write | Boolean | Blocks the creation of VPN configurations | - |
| WallpaperBlockModification | Write | Boolean | Block wallpaper from being changed. | - |
| WiFiConnectOnlyToConfiguredNetworks | Write | Boolean | Force the device to use only Wi-Fi networks set up through configuration profiles. | - |
| WiFiConnectToAllowedNetworksOnlyForced | Write | Boolean | Require devices to use Wi-Fi networks set up via configuration profiles. Available for devices running iOS and iPadOS versions 14.5 and later. | - |
| WifiPowerOnForced | Write | Boolean | Wi-Fi can't be turned off in the Settings app or in the Control Center, even when the device is in airplane mode. Available for iOS/iPadOS 13.0 and later. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphapplistitem

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | odatatype of the item. | `#microsoft.graph.appleAppListItem` |
| appId | Write | String | Kiosk mode managed app id | - |
| appStoreUrl | Write | String | Define the app store URL. | - |
| name | Write | String | Define the name of the app. | - |
| publisher | Write | String | Define the publisher of the app. | - |

#### MSFT\_MicrosoftGraphmediacontentratingaustralia

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| movieRating | Write | String | Movies rating selected for Australia | `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `mature`, `agesAbove15`, `agesAbove18` |
| tvRating | Write | String | TV rating selected for Australia | `allAllowed`, `allBlocked`, `preschoolers`, `children`, `general`, `parentalGuidance`, `mature`, `agesAbove15`, `agesAbove15AdultViolence` |

#### MSFT\_MicrosoftGraphmediacontentratingcanada

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| movieRating | Write | String | Movies rating selected for Canada | `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `agesAbove14`, `agesAbove18`, `restricted` |
| tvRating | Write | String | TV rating selected for Canada | `allAllowed`, `allBlocked`, `children`, `childrenAbove8`, `general`, `parentalGuidance`, `agesAbove14`, `agesAbove18` |

#### MSFT\_MicrosoftGraphmediacontentratingfrance

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| movieRating | Write | String | Movies rating selected for France | `allAllowed`, `allBlocked`, `agesAbove10`, `agesAbove12`, `agesAbove16`, `agesAbove18` |
| tvRating | Write | String | TV rating selected for France | `allAllowed`, `allBlocked`, `agesAbove10`, `agesAbove12`, `agesAbove16`, `agesAbove18` |

#### MSFT\_MicrosoftGraphmediacontentratinggermany

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| movieRating | Write | String | Movies rating selected for Germany | `allAllowed`, `allBlocked`, `general`, `agesAbove6`, `agesAbove12`, `agesAbove16`, `adults` |
| tvRating | Write | String | TV rating selected for Germany | `allAllowed`, `allBlocked`, `general`, `agesAbove6`, `agesAbove12`, `agesAbove16`, `adults` |

#### MSFT\_MicrosoftGraphmediacontentratingireland

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| movieRating | Write | String | Movies rating selected for Ireland | `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `agesAbove12`, `agesAbove15`, `agesAbove16`, `adults` |
| tvRating | Write | String | TV rating selected for Ireland | `allAllowed`, `allBlocked`, `general`, `children`, `youngAdults`, `parentalSupervision`, `mature` |

#### MSFT\_MicrosoftGraphmediacontentratingjapan

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| movieRating | Write | String | Movies rating selected for Japan | `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `agesAbove15`, `agesAbove18` |
| tvRating | Write | String | TV rating selected for Japan | `allAllowed`, `allBlocked`, `explicitAllowed` |

#### MSFT\_MicrosoftGraphmediacontentratingnewzealand

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| movieRating | Write | String | Movies rating selected for New Zealand | `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `mature`, `agesAbove13`, `agesAbove15`, `agesAbove16`, `agesAbove18`, `restricted`, `agesAbove16Restricted` |
| tvRating | Write | String | TV rating selected for New Zealand | `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `adults` |

#### MSFT\_MicrosoftGraphmediacontentratingunitedkingdom

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| movieRating | Write | String | Movies rating selected for UK | `allAllowed`, `allBlocked`, `general`, `universalChildren`, `parentalGuidance`, `agesAbove12Video`, `agesAbove12Cinema`, `agesAbove15`, `adults` |
| tvRating | Write | String | TV rating selected for UK | `allAllowed`, `allBlocked`, `caution` |

#### MSFT\_MicrosoftGraphmediacontentratingunitedstates

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| movieRating | Write | String | Movies rating selected for USA | `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `parentalGuidance13`, `restricted`, `adults` |
| tvRating | Write | String | TV rating selected for USA | `allAllowed`, `allBlocked`, `childrenAll`, `childrenAbove7`, `general`, `parentalGuidance`, `childrenAbove14`, `adults` |

#### MSFT\_MicrosoftGraphiosnetworkusagerule

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| cellularDataBlocked | Write | Boolean | If set to true, corresponding managed apps will not be allowed to use cellular data at any time. | - |
| cellularDataBlockWhenRoaming | Write | Boolean | If set to true, corresponding managed apps will not be allowed to use cellular data when roaming. | - |
| managedApps | Write | MSFT\_MicrosoftGraphapplistitem\[\] | Information about the managed apps that this rule is going to apply to. | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationPolicymacOS resource type

### Description

This resource configures an Intune device configuration profile for an MacOS Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune policy. | - |
| DisplayName | Key | String | Display name of the Intune policy. | - |
| Description | Write | String | Description of the Intune policy. | - |
| AddingGameCenterFriendsBlocked | Write | Boolean | Configures users from adding friends to Game Center. Available for devices running macOS versions 10.13 and later. | - |
| AirDropBlocked | Write | Boolean | Configures whether or not to allow AirDrop. | - |
| AppleWatchBlockAutoUnlock | Write | Boolean | Blocks users from unlocking their Mac with Apple Watch. | - |
| CameraBlocked | Write | Boolean | Blocks users from taking photographs and videos. | - |
| ClassroomAppBlockRemoteScreenObservation | Write | Boolean | Blocks AirPlay, screen sharing to other devices, and a Classroom app feature used by teachers to view their students' screens. This setting isn't available if you've blocked screenshots. | - |
| ClassroomAppForceUnpromptedScreenObservation | Write | Boolean | Unprompted observation means that teachers can view screens without warning students first. This setting isn't available if you've blocked screenshots. | - |
| ClassroomForceAutomaticallyJoinClasses | Write | Boolean | Students can join a class without prompting the teacher. | - |
| ClassroomForceRequestPermissionToLeaveClasses | Write | Boolean | Students enrolled in an unmanaged Classroom course must get teacher consent to leave the course. | - |
| ClassroomForceUnpromptedAppAndDeviceLock | Write | Boolean | Teachers can lock a student's device or app without the student's approval. | - |
| CompliantAppListType | Write | String | Device compliance can be viewed in the Restricted Apps Compliance report. | `none`, `appsInListCompliant`, `appsNotInListCompliant` |
| CompliantAppsList | Write | MSFT\_MicrosoftGraphapplistitemMacOS\[\] | List of apps in the compliance \(either allow list or block list, controlled by CompliantAppListType\). | - |
| ContentCachingBlocked | Write | Boolean | Configures whether or not to allow content caching. | - |
| DefinitionLookupBlocked | Write | Boolean | Block look up, a feature that looks up the definition of a highlighted word. | - |
| EmailInDomainSuffixes | Write | StringArray\[\] | Emails that the user sends or receives which don't match the domains you specify here will be marked as untrusted. | - |
| EraseContentAndSettingsBlocked | Write | Boolean | Configures the reset option on supervised devices. Available for devices running macOS versions 12.0 and later. | - |
| GameCenterBlocked | Write | Boolean | Configured if the Game Center icon is removed from the Home screen. Available for devices running macOS versions 10.13 and later. | - |
| ICloudBlockActivityContinuation | Write | Boolean | Handoff lets users start work on one MacOS device, and continue it on another MacOS or iOS device. Available for macOS 10.15 and later. | - |
| ICloudBlockAddressBook | Write | Boolean | Blocks iCloud from syncing contacts. | - |
| ICloudBlockBookmarks | Write | Boolean | Blocks iCloud from syncing bookmarks. | - |
| ICloudBlockCalendar | Write | Boolean | Blocks iCloud from syncing calendars. | - |
| ICloudBlockDocumentSync | Write | Boolean | Blocks iCloud from syncing documents and data. | - |
| ICloudBlockMail | Write | Boolean | Blocks iCloud from syncing mail. | - |
| ICloudBlockNotes | Write | Boolean | Blocks iCloud from syncing notes. | - |
| ICloudBlockPhotoLibrary | Write | Boolean | Any photos not fully downloaded from iCloud Photo Library to device will be removed from local storage. | - |
| ICloudBlockReminders | Write | Boolean | Blocks iCloud from syncing reminders. | - |
| ICloudDesktopAndDocumentsBlocked | Write | Boolean | Configures if the synchronization of cloud desktop and documents is blocked. Available for devices running macOS 10.12.4 and later. | - |
| ICloudPrivateRelayBlocked | Write | Boolean | Configures if iCloud private relay is blocked or not. Available for devices running macOS 12 and later. | - |
| ITunesBlockFileSharing | Write | Boolean | Blocks files from being transferred using iTunes. | - |
| ITunesBlockMusicService | Write | Boolean | Configures whether or not to block files from being transferred using iTunes. | - |
| KeyboardBlockDictation | Write | Boolean | Block dictation, which is a feature that converts the user's voice to text. | - |
| KeychainBlockCloudSync | Write | Boolean | Disables syncing credentials stored in the Keychain to iCloud | - |
| MultiplayerGamingBlocked | Write | Boolean | Configures whether multiplayer gaming when using Game Center is blocked. Available for devices running macOS versions 10.13 and later. | - |
| PasswordBlockAirDropSharing | Write | Boolean | Configures whether or not to block sharing passwords with the AirDrop passwords feature. | - |
| PasswordBlockAutoFill | Write | Boolean | Configures whether or not to block the AutoFill Passwords feature. | - |
| PasswordBlockFingerprintUnlock | Write | Boolean | Requires user to set a non-biometric passcode or password to unlock the device. | - |
| PasswordBlockModification | Write | Boolean | Blocks user from changing the set passcode. | - |
| PasswordBlockProximityRequests | Write | Boolean | Configures whether or not to block requesting passwords from nearby devices. | - |
| PasswordBlockSimple | Write | Boolean | Block simple password sequences, such as 1234 or 1111. | - |
| PasswordExpirationDays | Write | UInt32 | Number of days until device password must be changed. \(1-65535\) | - |
| PasswordMaximumAttemptCount | Write | UInt32 | Configures the number of allowed failed attempts to enter the passcode at the device's lock screen. Valid values 2 to 11 | - |
| PasswordMinimumCharacterSetCount | Write | UInt32 | Minimum number \(0-4\) of non-alphanumeric characters, such as #, %, !, etc., required in the password. The default value is 0. | - |
| PasswordMinimumLength | Write | UInt32 | Minimum number of digits or characters in password \(4-16\). | - |
| PasswordMinutesOfInactivityBeforeLock | Write | UInt32 | Set to 0 to require a password immediately. there's no maximum number of minutes, and this number overrides the number currently set on the device. | - |
| PasswordMinutesOfInactivityBeforeScreenTimeout | Write | UInt32 | Set to 0 to use the device's minimum possible value. This number \(0-60 minutes\) overrides the number currently set on the device. | - |
| PasswordMinutesUntilFailedLoginReset | Write | UInt32 | Configures the number of minutes before the login is reset after the maximum number of unsuccessful login attempts is reached. | - |
| PasswordPreviousPasswordBlockCount | Write | UInt32 | Number of new passwords that must be used until an old one can be reused. \(1-24\) | - |
| PasswordRequired | Write | Boolean | Specify the type of password required. | - |
| PasswordRequiredType | Write | String | Specify the type of password required. | `deviceDefault`, `alphanumeric`, `numeric` |
| PrivacyAccessControls | Write | MSFT\_MicrosoftGraphmacosprivacyaccesscontrolitem\[\] | Configure an app's access to specific data, folders, and apps on a device. These settings apply to devices running macOS Mojave 10.14 and later. | - |
| SafariBlockAutofill | Write | Boolean | Blocks Safari from remembering what users enter in web forms. | - |
| ScreenCaptureBlocked | Write | Boolean | Configures whether or not to block the user from taking Screenshots. | - |
| SoftwareUpdateMajorOSDeferredInstallDelayInDays | Write | UInt32 | Specify the number of days \(1-90\) to delay visibility of major OS software updates. Available for devices running macOS versions 11.3 and later. Valid values 0 to 90 | - |
| SoftwareUpdateMinorOSDeferredInstallDelayInDays | Write | UInt32 | Specify the number of days \(1-90\) to delay visibility of minor OS software updates. Available for devices running macOS versions 11.3 and later. Valid values 0 to 90 | - |
| SoftwareUpdateNonOSDeferredInstallDelayInDays | Write | UInt32 | Specify the number of days \(1-90\) to delay visibility of non-OS software updates. Available for devices running macOS versions 11.3 and later. Valid values 0 to 90 | - |
| SoftwareUpdatesEnforcedDelayInDays | Write | UInt32 | Delay the user's software update for this many days. The maximum is 90 days. \(1-90\) | - |
| SpotlightBlockInternetResults | Write | Boolean | Blocks Spotlight from returning any results from an Internet search | - |
| TouchIdTimeoutInHours | Write | UInt32 | Configures the maximum hours after which the user must enter their password to unlock the device instead of using Touch ID. Available for devices running macOS 12 and later. Valid values 0 to 2147483647 | - |
| UpdateDelayPolicy | Write | StringArray\[\] | Configures whether to delay OS and/or app updates for macOS. | `none`, `delayOSUpdateVisibility`, `delayAppUpdateVisibility`, `unknownFutureValue`, `delayMajorOsUpdateVisibility` |
| WallpaperModificationBlocked | Write | Boolean | Configures whether the wallpaper can be changed. Available for devices running macOS versions 10.13 and later. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphapplistitemMacOS

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | Specify the odataType | `#microsoft.graph.appleAppListItem` |
| appId | Write | String | The application or bundle identifier of the application | - |
| appStoreUrl | Write | String | The Store URL of the application | - |
| name | Write | String | The application name | - |
| publisher | Write | String | The publisher of the application | - |

#### MSFT\_MicrosoftGraphmacosprivacyaccesscontrolitem

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| accessibility | Write | String | Allow the app or process to control the Mac via the Accessibility subsystem. | `notConfigured`, `enabled`, `disabled` |
| addressBook | Write | String | Allow or block access to contact information managed by Contacts. | `notConfigured`, `enabled`, `disabled` |
| appleEventsAllowedReceivers | Write | MSFT\_MicrosoftGraphmacosappleeventreceiver\[\] | Allow or deny the app or process to send a restricted Apple event to another app or process. You will need to know the identifier, identifier type, and code requirement of the receiving app or process. | - |
| blockCamera | Write | Boolean | Block access to camera app. | - |
| blockListenEvent | Write | Boolean | Block the app or process from listening to events from input devices such as mouse, keyboard, and trackpad.Requires macOS 10.15 or later. | - |
| blockMicrophone | Write | Boolean | Block access to microphone. | - |
| blockScreenCapture | Write | Boolean | Block app from capturing contents of system display. Requires macOS 10.15 or later. | - |
| calendar | Write | String | Allow or block access to event information managed by Calendar. | `notConfigured`, `enabled`, `disabled` |
| codeRequirement | Write | String | Enter the code requirement, which can be obtained with the command 'codesign -display -r -' in the Terminal app. Include everything after '=>'. | - |
| displayName | Write | String | The display name of the app, process, or executable. | - |
| fileProviderPresence | Write | String | Allow the app or process to access files managed by another app's file provider extension. Requires macOS 10.15 or later. | `notConfigured`, `enabled`, `disabled` |
| identifier | Write | String | The bundle ID or path of the app, process, or executable. | - |
| identifierType | Write | String | A bundle ID is used to identify an app. A path is used to identify a process or executable. | `bundleID`, `path` |
| mediaLibrary | Write | String | Allow or block access to music and the media library. | `notConfigured`, `enabled`, `disabled` |
| photos | Write | String | Allow or block access to images managed by Photos. | `notConfigured`, `enabled`, `disabled` |
| postEvent | Write | String | Control access to CoreGraphics APIs, which are used to send CGEvents to the system event stream. | `notConfigured`, `enabled`, `disabled` |
| reminders | Write | String | Allow or block access to information managed by Reminders. | `notConfigured`, `enabled`, `disabled` |
| speechRecognition | Write | String | Allow or block access to system speech recognition facility. | `notConfigured`, `enabled`, `disabled` |
| staticCodeValidation | Write | Boolean | Statically validates the code requirement. Use this setting if the process invalidates its dynamic code signature. | - |
| systemPolicyAllFiles | Write | String | Control access to all protected files on a device. Files might be in locations such as emails, messages, apps, and administrative settings. Apply this setting with caution. | `notConfigured`, `enabled`, `disabled` |
| systemPolicyDesktopFolder | Write | String | Allow or block access to Desktop folder. | `notConfigured`, `enabled`, `disabled` |
| systemPolicyDocumentsFolder | Write | String | Allow or block access to Documents folder. | `notConfigured`, `enabled`, `disabled` |
| systemPolicyDownloadsFolder | Write | String | Allow or block access to Downloads folder. | `notConfigured`, `enabled`, `disabled` |
| systemPolicyNetworkVolumes | Write | String | Allow or block access to network volumes. Requires macOS 10.15 or later. | `notConfigured`, `enabled`, `disabled` |
| systemPolicyRemovableVolumes | Write | String | Control access to removable volumes on the device, such as an external hard drive. Requires macOS 10.15 or later. | `notConfigured`, `enabled`, `disabled` |
| systemPolicySystemAdminFiles | Write | String | Allow app or process to access files used in system administration. | `notConfigured`, `enabled`, `disabled` |

#### MSFT\_MicrosoftGraphmacosappleeventreceiver

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| allowed | Write | Boolean | Allow or block this app from receiving Apple events. | - |
| codeRequirement | Write | String | Code requirement for the app or binary that receives the Apple Event. | - |
| identifier | Write | String | Bundle ID of the app or file path of the process or executable that receives the Apple Event. | - |
| identifierType | Write | String | Use bundle ID for an app or path for a process or executable that receives the Apple Event. | `bundleID`, `path` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationPolicyWindows10 resource type

### Description

Intune Device Configuration Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AccountsBlockAddingNonMicrosoftAccountEmail | Write | Boolean | Indicates whether or not to Block the user from adding email accounts to the device that are not associated with a Microsoft account. | - |
| ActivateAppsWithVoice | Write | String | Specifies if Windows apps can be activated by voice. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| AntiTheftModeBlocked | Write | Boolean | Indicates whether or not to block the user from selecting an AntiTheft mode preference \(Windows 10 Mobile only\). | - |
| AppManagementMSIAllowUserControlOverInstall | Write | Boolean | This policy setting permits users to change installation options that typically are available only to system administrators. | - |
| AppManagementMSIAlwaysInstallWithElevatedPrivileges | Write | Boolean | This policy setting directs Windows Installer to use elevated permissions when it installs any program on the system. | - |
| AppManagementPackageFamilyNamesToLaunchAfterLogOn | Write | StringArray\[\] | List of semi-colon delimited Package Family Names of Windows apps. Listed Windows apps are to be launched after logon. | - |
| AppsAllowTrustedAppsSideloading | Write | String | Indicates whether apps from AppX packages signed with a trusted certificate can be side loaded. Possible values are: notConfigured, blocked, allowed. | `notConfigured`, `blocked`, `allowed` |
| AppsBlockWindowsStoreOriginatedApps | Write | Boolean | Indicates whether or not to disable the launch of all apps from Windows Store that came pre-installed or were downloaded. | - |
| AuthenticationAllowSecondaryDevice | Write | Boolean | Allows secondary authentication devices to work with Windows. | - |
| AuthenticationPreferredAzureADTenantDomainName | Write | String | Specifies the preferred domain among available domains in the Microsoft Entra tenant. | - |
| AuthenticationWebSignIn | Write | String | Indicates whether or not Web Credential Provider will be enabled. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| BluetoothAllowedServices | Write | StringArray\[\] | Specify a list of allowed Bluetooth services and profiles in hex formatted strings. | - |
| BluetoothBlockAdvertising | Write | Boolean | Whether or not to Block the user from using bluetooth advertising. | - |
| BluetoothBlockDiscoverableMode | Write | Boolean | Whether or not to Block the user from using bluetooth discoverable mode. | - |
| BluetoothBlocked | Write | Boolean | Whether or not to Block the user from using bluetooth. | - |
| BluetoothBlockPrePairing | Write | Boolean | Whether or not to block specific bundled Bluetooth peripherals to automatically pair with the host device. | - |
| BluetoothBlockPromptedProximalConnections | Write | Boolean | Whether or not to block the users from using Swift Pair and other proximity based scenarios. | - |
| CameraBlocked | Write | Boolean | Whether or not to Block the user from accessing the camera of the device. | - |
| CellularBlockDataWhenRoaming | Write | Boolean | Whether or not to Block the user from using data over cellular while roaming. | - |
| CellularBlockVpn | Write | Boolean | Whether or not to Block the user from using VPN over cellular. | - |
| CellularBlockVpnWhenRoaming | Write | Boolean | Whether or not to Block the user from using VPN when roaming over cellular. | - |
| CellularData | Write | String | Whether or not to allow the cellular data channel on the device. If not configured, the cellular data channel is allowed and the user can turn it off. Possible values are: blocked, required, allowed, notConfigured. | `blocked`, `required`, `allowed`, `notConfigured` |
| CertificatesBlockManualRootCertificateInstallation | Write | Boolean | Whether or not to Block the user from doing manual root certificate installation. | - |
| ConfigureTimeZone | Write | String | Specifies the time zone to be applied to the device. This is the standard Windows name for the target time zone. | - |
| ConnectedDevicesServiceBlocked | Write | Boolean | Whether or not to block Connected Devices Service which enables discovery and connection to other devices, remote messaging, remote app sessions and other cross-device experiences. | - |
| CopyPasteBlocked | Write | Boolean | Whether or not to Block the user from using copy paste. | - |
| CortanaBlocked | Write | Boolean | Whether or not to Block the user from using Cortana. | - |
| CryptographyAllowFipsAlgorithmPolicy | Write | Boolean | Specify whether to allow or disallow the Federal Information Processing Standard \(FIPS\) policy. | - |
| DataProtectionBlockDirectMemoryAccess | Write | Boolean | This policy setting allows you to block direct memory access \(DMA\) for all hot pluggable PCI downstream ports until a user logs into Windows. | - |
| DefenderBlockEndUserAccess | Write | Boolean | Whether or not to block end user access to Defender. | - |
| DefenderBlockOnAccessProtection | Write | Boolean | Allows or disallows Windows Defender On Access Protection functionality. | - |
| DefenderCloudBlockLevel | Write | String | Specifies the level of cloud-delivered protection. Possible values are: notConfigured, high, highPlus, zeroTolerance. | `notConfigured`, `high`, `highPlus`, `zeroTolerance` |
| DefenderCloudExtendedTimeout | Write | UInt32 | Timeout extension for file scanning by the cloud. Valid values 0 to 50 | - |
| DefenderCloudExtendedTimeoutInSeconds | Write | UInt32 | Timeout extension for file scanning by the cloud. Valid values 0 to 50 | - |
| DefenderDaysBeforeDeletingQuarantinedMalware | Write | UInt32 | Number of days before deleting quarantined malware. Valid values 0 to 90 | - |
| DefenderDetectedMalwareActions | Write | MSFT\_MicrosoftGraphdefenderDetectedMalwareActions1 | Gets or sets Defenders actions to take on detected Malware per threat level. | - |
| DefenderDisableCatchupFullScan | Write | Boolean | When blocked, catch-up scans for scheduled full scans will be turned off. | - |
| DefenderDisableCatchupQuickScan | Write | Boolean | When blocked, catch-up scans for scheduled quick scans will be turned off. | - |
| DefenderFileExtensionsToExclude | Write | StringArray\[\] | File extensions to exclude from scans and real time protection. | - |
| DefenderFilesAndFoldersToExclude | Write | StringArray\[\] | Files and folder to exclude from scans and real time protection. | - |
| DefenderMonitorFileActivity | Write | String | Value for monitoring file activity. Possible values are: userDefined, disable, monitorAllFiles, monitorIncomingFilesOnly, monitorOutgoingFilesOnly. | `userDefined`, `disable`, `monitorAllFiles`, `monitorIncomingFilesOnly`, `monitorOutgoingFilesOnly` |
| DefenderPotentiallyUnwantedAppAction | Write | String | Gets or sets Defenders action to take on Potentially Unwanted Application \(PUA\), which includes software with behaviors of ad-injection, software bundling, persistent solicitation for payment or subscription, etc. Defender alerts user when PUA is being downloaded or attempts to install itself. Added in Windows 10 for desktop. Possible values are: deviceDefault, block, audit. | `deviceDefault`, `block`, `audit` |
| DefenderPotentiallyUnwantedAppActionSetting | Write | String | Gets or sets Defenders action to take on Potentially Unwanted Application \(PUA\), which includes software with behaviors of ad-injection, software bundling, persistent solicitation for payment or subscription, etc. Defender alerts user when PUA is being downloaded or attempts to install itself. Added in Windows 10 for desktop. Possible values are: userDefined, enable, auditMode, warn, notConfigured. | `userDefined`, `enable`, `auditMode`, `warn`, `notConfigured` |
| DefenderProcessesToExclude | Write | StringArray\[\] | Processes to exclude from scans and real time protection. | - |
| DefenderPromptForSampleSubmission | Write | String | The configuration for how to prompt user for sample submission. Possible values are: userDefined, alwaysPrompt, promptBeforeSendingPersonalData, neverSendData, sendAllDataWithoutPrompting. | `userDefined`, `alwaysPrompt`, `promptBeforeSendingPersonalData`, `neverSendData`, `sendAllDataWithoutPrompting` |
| DefenderRequireBehaviorMonitoring | Write | Boolean | Indicates whether or not to require behavior monitoring. | - |
| DefenderRequireCloudProtection | Write | Boolean | Indicates whether or not to require cloud protection. | - |
| DefenderRequireNetworkInspectionSystem | Write | Boolean | Indicates whether or not to require network inspection system. | - |
| DefenderRequireRealTimeMonitoring | Write | Boolean | Indicates whether or not to require real time monitoring. | - |
| DefenderScanArchiveFiles | Write | Boolean | Indicates whether or not to scan archive files. | - |
| DefenderScanDownloads | Write | Boolean | Indicates whether or not to scan downloads. | - |
| DefenderScanIncomingMail | Write | Boolean | Indicates whether or not to scan incoming mail messages. | - |
| DefenderScanMappedNetworkDrivesDuringFullScan | Write | Boolean | Indicates whether or not to scan mapped network drives during full scan. | - |
| DefenderScanMaxCpu | Write | UInt32 | Max CPU usage percentage during scan. Valid values 0 to 100 | - |
| DefenderScanNetworkFiles | Write | Boolean | Indicates whether or not to scan files opened from a network folder. | - |
| DefenderScanRemovableDrivesDuringFullScan | Write | Boolean | Indicates whether or not to scan removable drives during full scan. | - |
| DefenderScanScriptsLoadedInInternetExplorer | Write | Boolean | Indicates whether or not to scan scripts loaded in Internet Explorer browser. | - |
| DefenderScanType | Write | String | The defender system scan type. Possible values are: userDefined, disabled, quick, full. | `userDefined`, `disabled`, `quick`, `full` |
| DefenderScheduledQuickScanTime | Write | String | The time to perform a daily quick scan. | - |
| DefenderScheduledScanTime | Write | String | The defender time for the system scan. | - |
| DefenderScheduleScanEnableLowCpuPriority | Write | Boolean | When enabled, low CPU priority will be used during scheduled scans. | - |
| DefenderSignatureUpdateIntervalInHours | Write | UInt32 | The signature update interval in hours. Specify 0 not to check. Valid values 0 to 24 | - |
| DefenderSubmitSamplesConsentType | Write | String | Checks for the user consent level in Windows Defender to send data. Possible values are: sendSafeSamplesAutomatically, alwaysPrompt, neverSend, sendAllSamplesAutomatically. | `sendSafeSamplesAutomatically`, `alwaysPrompt`, `neverSend`, `sendAllSamplesAutomatically` |
| DefenderSystemScanSchedule | Write | String | Defender day of the week for the system scan. Possible values are: userDefined, everyday, sunday, monday, tuesday, wednesday, thursday, friday, saturday, noScheduledScan. | `userDefined`, `everyday`, `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday`, `noScheduledScan` |
| DeveloperUnlockSetting | Write | String | Indicates whether or not to allow developer unlock. Possible values are: notConfigured, blocked, allowed. | `notConfigured`, `blocked`, `allowed` |
| DeviceManagementBlockFactoryResetOnMobile | Write | Boolean | Indicates whether or not to Block the user from resetting their phone. | - |
| DeviceManagementBlockManualUnenroll | Write | Boolean | Indicates whether or not to Block the user from doing manual un-enrollment from device management. | - |
| DiagnosticsDataSubmissionMode | Write | String | Gets or sets a value allowing the device to send diagnostic and usage telemetry data, such as Watson. Possible values are: userDefined, none, basic, enhanced, full. | `userDefined`, `none`, `basic`, `enhanced`, `full` |
| DisplayAppListWithGdiDPIScalingTurnedOff | Write | StringArray\[\] | List of legacy applications that have GDI DPI Scaling turned off. | - |
| DisplayAppListWithGdiDPIScalingTurnedOn | Write | StringArray\[\] | List of legacy applications that have GDI DPI Scaling turned on. | - |
| EdgeAllowStartPagesModification | Write | Boolean | Allow users to change Start pages on Edge. Use the EdgeHomepageUrls to specify the Start pages that the user would see by default when they open Edge. | - |
| EdgeBlockAccessToAboutFlags | Write | Boolean | Indicates whether or not to prevent access to about flags on Edge browser. | - |
| EdgeBlockAddressBarDropdown | Write | Boolean | Block the address bar dropdown functionality in Microsoft Edge. Disable this settings to minimize network connections from Microsoft Edge to Microsoft services. | - |
| EdgeBlockAutofill | Write | Boolean | Indicates whether or not to block auto fill. | - |
| EdgeBlockCompatibilityList | Write | Boolean | Block Microsoft compatibility list in Microsoft Edge. This list from Microsoft helps Edge properly display sites with known compatibility issues. | - |
| EdgeBlockDeveloperTools | Write | Boolean | Indicates whether or not to block developer tools in the Edge browser. | - |
| EdgeBlocked | Write | Boolean | Indicates whether or not to Block the user from using the Edge browser. | - |
| EdgeBlockEditFavorites | Write | Boolean | Indicates whether or not to Block the user from making changes to Favorites. | - |
| EdgeBlockExtensions | Write | Boolean | Indicates whether or not to block extensions in the Edge browser. | - |
| EdgeBlockFullScreenMode | Write | Boolean | Allow or prevent Edge from entering the full screen mode. | - |
| EdgeBlockInPrivateBrowsing | Write | Boolean | Indicates whether or not to block InPrivate browsing on corporate networks, in the Edge browser. | - |
| EdgeBlockJavaScript | Write | Boolean | Indicates whether or not to Block the user from using JavaScript. | - |
| EdgeBlockLiveTileDataCollection | Write | Boolean | Block the collection of information by Microsoft for live tile creation when users pin a site to Start from Microsoft Edge. | - |
| EdgeBlockPasswordManager | Write | Boolean | Indicates whether or not to Block password manager. | - |
| EdgeBlockPopups | Write | Boolean | Indicates whether or not to block popups. | - |
| EdgeBlockPrelaunch | Write | Boolean | Decide whether Microsoft Edge is prelaunched at Windows startup. | - |
| EdgeBlockPrinting | Write | Boolean | Configure Edge to allow or block printing. | - |
| EdgeBlockSavingHistory | Write | Boolean | Configure Edge to allow browsing history to be saved or to never save browsing history. | - |
| EdgeBlockSearchEngineCustomization | Write | Boolean | Indicates whether or not to block the user from adding new search engine or changing the default search engine. | - |
| EdgeBlockSearchSuggestions | Write | Boolean | Indicates whether or not to block the user from using the search suggestions in the address bar. | - |
| EdgeBlockSendingDoNotTrackHeader | Write | Boolean | Indicates whether or not to Block the user from sending the do not track header. | - |
| EdgeBlockSendingIntranetTrafficToInternetExplorer | Write | Boolean | Indicates whether or not to switch the intranet traffic from Edge to Internet Explorer. Note: the name of this property is misleading the property is obsolete, use EdgeSendIntranetTrafficToInternetExplorer instead. | - |
| EdgeBlockSideloadingExtensions | Write | Boolean | Indicates whether the user can sideload extensions. | - |
| EdgeBlockTabPreloading | Write | Boolean | Configure whether Edge preloads the new tab page at Windows startup. | - |
| EdgeBlockWebContentOnNewTabPage | Write | Boolean | Configure to load a blank page in Edge instead of the default New tab page and prevent users from changing it. | - |
| EdgeClearBrowsingDataOnExit | Write | Boolean | Clear browsing data on exiting Microsoft Edge. | - |
| EdgeCookiePolicy | Write | String | Indicates which cookies to block in the Edge browser. Possible values are: userDefined, allow, blockThirdParty, blockAll. | `userDefined`, `allow`, `blockThirdParty`, `blockAll` |
| EdgeDisableFirstRunPage | Write | Boolean | Block the Microsoft web page that opens on the first use of Microsoft Edge. This policy allows enterprises, like those enrolled in zero emissions configurations, to block this page. | - |
| EdgeEnterpriseModeSiteListLocation | Write | String | Indicates the enterprise mode site list location. Could be a local file, local network or http location. | - |
| EdgeFavoritesBarVisibility | Write | String | Get or set a value that specifies whether to set the favorites bar to always be visible or hidden on any page. Possible values are: notConfigured, hide, show. | `notConfigured`, `hide`, `show` |
| EdgeFavoritesListLocation | Write | String | The location of the favorites list to provision. Could be a local file, local network or http location. | - |
| EdgeFirstRunUrl | Write | String | The first run URL for when Edge browser is opened for the first time. | - |
| EdgeHomeButtonConfiguration | Write | MSFT\_MicrosoftGraphedgeHomeButtonConfiguration | Causes the Home button to either hide, load the default Start page, load a New tab page, or a custom URL | - |
| EdgeHomeButtonConfigurationEnabled | Write | Boolean | Enable the Home button configuration. | - |
| EdgeHomepageUrls | Write | StringArray\[\] | The list of URLs for homepages shodwn on MDM-enrolled devices on Edge browser. | - |
| EdgeKioskModeRestriction | Write | String | Controls how the Microsoft Edge settings are restricted based on the configure kiosk mode. Possible values are: notConfigured, digitalSignage, normalMode, publicBrowsingSingleApp, publicBrowsingMultiApp. | `notConfigured`, `digitalSignage`, `normalMode`, `publicBrowsingSingleApp`, `publicBrowsingMultiApp` |
| EdgeKioskResetAfterIdleTimeInMinutes | Write | UInt32 | Specifies the time in minutes from the last user activity before Microsoft Edge kiosk resets. Valid values are 0-1440. The default is 5. 0 indicates no reset. Valid values 0 to 1440 | - |
| EdgeNewTabPageURL | Write | String | Specify the page opened when new tabs are created. | - |
| EdgeOpensWith | Write | String | Specify what kind of pages are open at start. Possible values are: notConfigured, startPage, newTabPage, previousPages, specificPages. | `notConfigured`, `startPage`, `newTabPage`, `previousPages`, `specificPages` |
| EdgePreventCertificateErrorOverride | Write | Boolean | Allow or prevent users from overriding certificate errors. | - |
| EdgeRequiredExtensionPackageFamilyNames | Write | StringArray\[\] | Specify the list of package family names of browser extensions that are required and can't be turned off by the user. | - |
| EdgeRequireSmartScreen | Write | Boolean | Indicates whether or not to Require the user to use the smart screen filter. | - |
| EdgeSearchEngine | Write | MSFT\_MicrosoftGraphedgeSearchEngineBase | Allows IT admins to set a default search engine for MDM-Controlled devices. Users can override this and change their default search engine provided the AllowSearchEngineCustomization policy is not set. | - |
| EdgeSendIntranetTrafficToInternetExplorer | Write | Boolean | Indicates whether or not to switch the intranet traffic from Edge to Internet Explorer. | - |
| EdgeShowMessageWhenOpeningInternetExplorerSites | Write | String | Controls the message displayed by Edge before switching to Internet Explorer. Possible values are: notConfigured, disabled, enabled, keepGoing. | `notConfigured`, `disabled`, `enabled`, `keepGoing` |
| EdgeSyncFavoritesWithInternetExplorer | Write | Boolean | Enable favorites sync between Internet Explorer and Microsoft Edge. Additions, deletions, modifications and order changes to favorites are shared between browsers. | - |
| EdgeTelemetryForMicrosoft365Analytics | Write | String | Specifies what type of telemetry data \(none, intranet, internet, both\) is sent to Microsoft 365 Analytics. Possible values are: notConfigured, intranet, internet, intranetAndInternet. | `notConfigured`, `intranet`, `internet`, `intranetAndInternet` |
| EnableAutomaticRedeployment | Write | Boolean | Allow users with administrative rights to delete all user data and settings using CTRL + Win + R at the device lock screen so that the device can be automatically re-configured and re-enrolled into management. | - |
| EnergySaverOnBatteryThresholdPercentage | Write | UInt32 | This setting allows you to specify battery charge level at which Energy Saver is turned on. While on battery, Energy Saver is automatically turned on at \(and below\) the specified battery charge level. Valid input range \(0-100\). Valid values 0 to 100 | - |
| EnergySaverPluggedInThresholdPercentage | Write | UInt32 | This setting allows you to specify battery charge level at which Energy Saver is turned on. While plugged in, Energy Saver is automatically turned on at \(and below\) the specified battery charge level. Valid input range \(0-100\). Valid values 0 to 100 | - |
| EnterpriseCloudPrintDiscoveryEndPoint | Write | String | Endpoint for discovering cloud printers. | - |
| EnterpriseCloudPrintDiscoveryMaxLimit | Write | UInt32 | Maximum number of printers that should be queried from a discovery endpoint. This is a mobile only setting. Valid values 1 to 65535 | - |
| EnterpriseCloudPrintMopriaDiscoveryResourceIdentifier | Write | String | OAuth resource URI for printer discovery service as configured in Azure portal. | - |
| EnterpriseCloudPrintOAuthAuthority | Write | String | Authentication endpoint for acquiring OAuth tokens. | - |
| EnterpriseCloudPrintOAuthClientIdentifier | Write | String | GUID of a client application authorized to retrieve OAuth tokens from the OAuth Authority. | - |
| EnterpriseCloudPrintResourceIdentifier | Write | String | OAuth resource URI for print service as configured in the Azure portal. | - |
| ExperienceBlockDeviceDiscovery | Write | Boolean | Indicates whether or not to enable device discovery UX. | - |
| ExperienceBlockErrorDialogWhenNoSIM | Write | Boolean | Indicates whether or not to allow the error dialog from displaying if no SIM card is detected. | - |
| ExperienceBlockTaskSwitcher | Write | Boolean | Indicates whether or not to enable task switching on the device. | - |
| ExperienceDoNotSyncBrowserSettings | Write | String | Allow or prevent the syncing of Microsoft Edge Browser settings. Option for IT admins to prevent syncing across devices, but allow user override. Possible values are: notConfigured, blockedWithUserOverride, blocked. | `notConfigured`, `blockedWithUserOverride`, `blocked` |
| FindMyFiles | Write | String | Controls if the user can configure search to Find My Files mode, which searches files in secondary hard drives and also outside of the user profile. Find My Files does not allow users to search files or locations to which they do not have access. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| GameDvrBlocked | Write | Boolean | Indicates whether or not to block DVR and broadcasting. | - |
| InkWorkspaceAccess | Write | String | Controls the user access to the ink workspace, from the desktop and from above the lock screen. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| InkWorkspaceAccessState | Write | String | Controls the user access to the ink workspace, from the desktop and from above the lock screen. Possible values are: notConfigured, blocked, allowed. | `notConfigured`, `blocked`, `allowed` |
| InkWorkspaceBlockSuggestedApps | Write | Boolean | Specify whether to show recommended app suggestions in the ink workspace. | - |
| InternetSharingBlocked | Write | Boolean | Indicates whether or not to Block the user from using internet sharing. | - |
| LocationServicesBlocked | Write | Boolean | Indicates whether or not to Block the user from location services. | - |
| LockScreenActivateAppsWithVoice | Write | String | This policy setting specifies whether Windows apps can be activated by voice while the system is locked. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| LockScreenAllowTimeoutConfiguration | Write | Boolean | Specify whether to show a user-configurable setting to control the screen timeout while on the lock screen of Windows 10 Mobile devices. If this policy is set to Allow, the value set by lockScreenTimeoutInSeconds is ignored. | - |
| LockScreenBlockActionCenterNotifications | Write | Boolean | Indicates whether or not to block action center notifications over lock screen. | - |
| LockScreenBlockCortana | Write | Boolean | Indicates whether or not the user can interact with Cortana using speech while the system is locked. | - |
| LockScreenBlockToastNotifications | Write | Boolean | Indicates whether to allow toast notifications above the device lock screen. | - |
| LockScreenTimeoutInSeconds | Write | UInt32 | Set the duration \(in seconds\) from the screen locking to the screen turning off for Windows 10 Mobile devices. Supported values are 11-1800. Valid values 11 to 1800 | - |
| LogonBlockFastUserSwitching | Write | Boolean | Disables the ability to quickly switch between users that are logged on simultaneously without logging off. | - |
| MessagingBlockMMS | Write | Boolean | Indicates whether or not to block the MMS send/receive functionality on the device. | - |
| MessagingBlockRichCommunicationServices | Write | Boolean | Indicates whether or not to block the RCS send/receive functionality on the device. | - |
| MessagingBlockSync | Write | Boolean | Indicates whether or not to block text message back up and restore and Messaging Everywhere. | - |
| MicrosoftAccountBlocked | Write | Boolean | Indicates whether or not to Block a Microsoft account. | - |
| MicrosoftAccountBlockSettingsSync | Write | Boolean | Indicates whether or not to Block Microsoft account settings sync. | - |
| MicrosoftAccountSignInAssistantSettings | Write | String | Controls the Microsoft Account Sign-In Assistant \(wlidsvc\) NT service. Possible values are: notConfigured, disabled. | `notConfigured`, `disabled` |
| NetworkProxyApplySettingsDeviceWide | Write | Boolean | If set, proxy settings will be applied to all processes and accounts in the device. Otherwise, it will be applied to the user account thats enrolled into MDM. | - |
| NetworkProxyAutomaticConfigurationUrl | Write | String | Address to the proxy auto-config \(PAC\) script you want to use. | - |
| NetworkProxyDisableAutoDetect | Write | Boolean | Disable automatic detection of settings. If enabled, the system will try to find the path to a proxy auto-config \(PAC\) script. | - |
| NetworkProxyServer | Write | MSFT\_MicrosoftGraphwindows10NetworkProxyServer | Specifies manual proxy server settings. | - |
| NfcBlocked | Write | Boolean | Indicates whether or not to Block the user from using near field communication. | - |
| OneDriveDisableFileSync | Write | Boolean | Gets or sets a value allowing IT admins to prevent apps and features from working with files on OneDrive. | - |
| PasswordBlockSimple | Write | Boolean | Specify whether PINs or passwords such as '1111' or '1234' are allowed. For Windows 10 desktops, it also controls the use of picture passwords. | - |
| PasswordExpirationDays | Write | UInt32 | The password expiration in days. Valid values 0 to 730 | - |
| PasswordMinimumAgeInDays | Write | UInt32 | This security setting determines the period of time \(in days\) that a password must be used before the user can change it. Valid values 0 to 998 | - |
| PasswordMinimumCharacterSetCount | Write | UInt32 | The number of character sets required in the password. | - |
| PasswordMinimumLength | Write | UInt32 | The minimum password length. Valid values 4 to 16 | - |
| PasswordMinutesOfInactivityBeforeScreenTimeout | Write | UInt32 | The minutes of inactivity before the screen times out. | - |
| PasswordPreviousPasswordBlockCount | Write | UInt32 | The number of previous passwords to prevent reuse of. Valid values 0 to 50 | - |
| PasswordRequired | Write | Boolean | Indicates whether or not to require the user to have a password. | - |
| PasswordRequiredType | Write | String | The required password type. Possible values are: deviceDefault, alphanumeric, numeric. | `deviceDefault`, `alphanumeric`, `numeric` |
| PasswordRequireWhenResumeFromIdleState | Write | Boolean | Indicates whether or not to require a password upon resuming from an idle state. | - |
| PasswordSignInFailureCountBeforeFactoryReset | Write | UInt32 | The number of sign in failures before factory reset. Valid values 0 to 999 | - |
| PersonalizationDesktopImageUrl | Write | String | A http or https Url to a jpg, jpeg or png image that needs to be downloaded and used as the Desktop Image or a file Url to a local image on the file system that needs to used as the Desktop Image. | - |
| PersonalizationLockScreenImageUrl | Write | String | A http or https Url to a jpg, jpeg or png image that neeeds to be downloaded and used as the Lock Screen Image or a file Url to a local image on the file system that needs to be used as the Lock Screen Image. | - |
| PowerButtonActionOnBattery | Write | String | This setting specifies the action that Windows takes when a user presses the Power button while on battery. Possible values are: notConfigured, noAction, sleep, hibernate, shutdown. | `notConfigured`, `noAction`, `sleep`, `hibernate`, `shutdown` |
| PowerButtonActionPluggedIn | Write | String | This setting specifies the action that Windows takes when a user presses the Power button while plugged in. Possible values are: notConfigured, noAction, sleep, hibernate, shutdown. | `notConfigured`, `noAction`, `sleep`, `hibernate`, `shutdown` |
| PowerHybridSleepOnBattery | Write | String | This setting allows you to turn off hybrid sleep while on battery. If you set this setting to disable, a hiberfile is not generated when the system transitions to sleep \(Stand By\). If you set this setting to enable or do not configure this policy setting, users control this setting. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| PowerHybridSleepPluggedIn | Write | String | This setting allows you to turn off hybrid sleep while plugged in. If you set this setting to disable, a hiberfile is not generated when the system transitions to sleep \(Stand By\). If you set this setting to enable or do not configure this policy setting, users control this setting. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| PowerLidCloseActionOnBattery | Write | String | This setting specifies the action that Windows takes when a user closes the lid on a mobile PC while on battery. Possible values are: notConfigured, noAction, sleep, hibernate, shutdown. | `notConfigured`, `noAction`, `sleep`, `hibernate`, `shutdown` |
| PowerLidCloseActionPluggedIn | Write | String | This setting specifies the action that Windows takes when a user closes the lid on a mobile PC while plugged in. Possible values are: notConfigured, noAction, sleep, hibernate, shutdown. | `notConfigured`, `noAction`, `sleep`, `hibernate`, `shutdown` |
| PowerSleepButtonActionOnBattery | Write | String | This setting specifies the action that Windows takes when a user presses the Sleep button while on battery. Possible values are: notConfigured, noAction, sleep, hibernate, shutdown. | `notConfigured`, `noAction`, `sleep`, `hibernate`, `shutdown` |
| PowerSleepButtonActionPluggedIn | Write | String | This setting specifies the action that Windows takes when a user presses the Sleep button while plugged in. Possible values are: notConfigured, noAction, sleep, hibernate, shutdown. | `notConfigured`, `noAction`, `sleep`, `hibernate`, `shutdown` |
| PrinterBlockAddition | Write | Boolean | Prevent user installation of additional printers from printers settings. | - |
| PrinterDefaultName | Write | String | Name \(network host name\) of an installed printer. | - |
| PrinterNames | Write | StringArray\[\] | Automatically provision printers based on their names \(network host names\). | - |
| PrivacyAdvertisingId | Write | String | Enables or disables the use of advertising ID. Added in Windows 10, version 1607. Possible values are: notConfigured, blocked, allowed. | `notConfigured`, `blocked`, `allowed` |
| PrivacyAutoAcceptPairingAndConsentPrompts | Write | Boolean | Indicates whether or not to allow the automatic acceptance of the pairing and privacy user consent dialog when launching apps. | - |
| PrivacyBlockActivityFeed | Write | Boolean | Blocks the usage of cloud based speech services for Cortana, Dictation, or Store applications. | - |
| PrivacyBlockInputPersonalization | Write | Boolean | Indicates whether or not to block the usage of cloud based speech services for Cortana, Dictation, or Store applications. | - |
| PrivacyBlockPublishUserActivities | Write | Boolean | Blocks the shared experiences/discovery of recently used resources in task switcher etc. | - |
| PrivacyDisableLaunchExperience | Write | Boolean | This policy prevents the privacy experience from launching during user logon for new and upgraded users. | - |
| ResetProtectionModeBlocked | Write | Boolean | Indicates whether or not to Block the user from reset protection mode. | - |
| SafeSearchFilter | Write | String | Specifies what filter level of safe search is required. Possible values are: userDefined, strict, moderate. | `userDefined`, `strict`, `moderate` |
| ScreenCaptureBlocked | Write | Boolean | Indicates whether or not to Block the user from taking Screenshots. | - |
| SearchBlockDiacritics | Write | Boolean | Specifies if search can use diacritics. | - |
| SearchBlockWebResults | Write | Boolean | Indicates whether or not to block the web search. | - |
| SearchDisableAutoLanguageDetection | Write | Boolean | Specifies whether to use automatic language detection when indexing content and properties. | - |
| SearchDisableIndexerBackoff | Write | Boolean | Indicates whether or not to disable the search indexer backoff feature. | - |
| SearchDisableIndexingEncryptedItems | Write | Boolean | Indicates whether or not to block indexing of WIP-protected items to prevent them from appearing in search results for Cortana or Explorer. | - |
| SearchDisableIndexingRemovableDrive | Write | Boolean | Indicates whether or not to allow users to add locations on removable drives to libraries and to be indexed. | - |
| SearchDisableLocation | Write | Boolean | Specifies if search can use location information. | - |
| SearchDisableUseLocation | Write | Boolean | Specifies if search can use location information. | - |
| SearchEnableAutomaticIndexSizeManangement | Write | Boolean | Specifies minimum amount of hard drive space on the same drive as the index location before indexing stops. | - |
| SearchEnableRemoteQueries | Write | Boolean | Indicates whether or not to block remote queries of this computers index. | - |
| SecurityBlockAzureADJoinedDevicesAutoEncryption | Write | Boolean | Specify whether to allow automatic device encryption during OOBE when the device is Microsoft Entra joined \(desktop only\). | - |
| SettingsBlockAccountsPage | Write | Boolean | Indicates whether or not to block access to Accounts in Settings app. | - |
| SettingsBlockAddProvisioningPackage | Write | Boolean | Indicates whether or not to block the user from installing provisioning packages. | - |
| SettingsBlockAppsPage | Write | Boolean | Indicates whether or not to block access to Apps in Settings app. | - |
| SettingsBlockChangeLanguage | Write | Boolean | Indicates whether or not to block the user from changing the language settings. | - |
| SettingsBlockChangePowerSleep | Write | Boolean | Indicates whether or not to block the user from changing power and sleep settings. | - |
| SettingsBlockChangeRegion | Write | Boolean | Indicates whether or not to block the user from changing the region settings. | - |
| SettingsBlockChangeSystemTime | Write | Boolean | Indicates whether or not to block the user from changing date and time settings. | - |
| SettingsBlockDevicesPage | Write | Boolean | Indicates whether or not to block access to Devices in Settings app. | - |
| SettingsBlockEaseOfAccessPage | Write | Boolean | Indicates whether or not to block access to Ease of Access in Settings app. | - |
| SettingsBlockEditDeviceName | Write | Boolean | Indicates whether or not to block the user from editing the device name. | - |
| SettingsBlockGamingPage | Write | Boolean | Indicates whether or not to block access to Gaming in Settings app. | - |
| SettingsBlockNetworkInternetPage | Write | Boolean | Indicates whether or not to block access to Network & Internet in Settings app. | - |
| SettingsBlockPersonalizationPage | Write | Boolean | Indicates whether or not to block access to Personalization in Settings app. | - |
| SettingsBlockPrivacyPage | Write | Boolean | Indicates whether or not to block access to Privacy in Settings app. | - |
| SettingsBlockRemoveProvisioningPackage | Write | Boolean | Indicates whether or not to block the runtime configuration agent from removing provisioning packages. | - |
| SettingsBlockSettingsApp | Write | Boolean | Indicates whether or not to block access to Settings app. | - |
| SettingsBlockSystemPage | Write | Boolean | Indicates whether or not to block access to System in Settings app. | - |
| SettingsBlockTimeLanguagePage | Write | Boolean | Indicates whether or not to block access to Time & Language in Settings app. | - |
| SettingsBlockUpdateSecurityPage | Write | Boolean | Indicates whether or not to block access to Update & Security in Settings app. | - |
| SharedUserAppDataAllowed | Write | Boolean | Indicates whether or not to block multiple users of the same app to share data. | - |
| SmartScreenAppInstallControl | Write | String | Added in Windows 10, version 1703. Allows IT Admins to control whether users are allowed to install apps from places other than the Store. Possible values are: notConfigured, anywhere, storeOnly, recommendations, preferStore. | `notConfigured`, `anywhere`, `storeOnly`, `recommendations`, `preferStore` |
| SmartScreenBlockPromptOverride | Write | Boolean | Indicates whether or not users can override SmartScreen Filter warnings about potentially malicious websites. | - |
| SmartScreenBlockPromptOverrideForFiles | Write | Boolean | Indicates whether or not users can override the SmartScreen Filter warnings about downloading unverified files | - |
| SmartScreenEnableAppInstallControl | Write | Boolean | This property will be deprecated in July 2019 and will be replaced by property SmartScreenAppInstallControl. Allows IT Admins to control whether users are allowed to install apps from places other than the Store. | - |
| StartBlockUnpinningAppsFromTaskbar | Write | Boolean | Indicates whether or not to block the user from unpinning apps from taskbar. | - |
| StartMenuAppListVisibility | Write | String | Setting the value of this collapses the app list, removes the app list entirely, or disables the corresponding toggle in the Settings app. Possible values are: userDefined, collapse, remove, disableSettingsApp. | `userDefined`, `collapse`, `remove`, `disableSettingsApp` |
| StartMenuHideChangeAccountSettings | Write | Boolean | Enabling this policy hides the change account setting from appearing in the user tile in the start menu. | - |
| StartMenuHideFrequentlyUsedApps | Write | Boolean | Enabling this policy hides the most used apps from appearing on the start menu and disables the corresponding toggle in the Settings app. | - |
| StartMenuHideHibernate | Write | Boolean | Enabling this policy hides hibernate from appearing in the power button in the start menu. | - |
| StartMenuHideLock | Write | Boolean | Enabling this policy hides lock from appearing in the user tile in the start menu. | - |
| StartMenuHidePowerButton | Write | Boolean | Enabling this policy hides the power button from appearing in the start menu. | - |
| StartMenuHideRecentJumpLists | Write | Boolean | Enabling this policy hides recent jump lists from appearing on the start menu/taskbar and disables the corresponding toggle in the Settings app. | - |
| StartMenuHideRecentlyAddedApps | Write | Boolean | Enabling this policy hides recently added apps from appearing on the start menu and disables the corresponding toggle in the Settings app. | - |
| StartMenuHideRestartOptions | Write | Boolean | Enabling this policy hides 'Restart/Update and Restart' from appearing in the power button in the start menu. | - |
| StartMenuHideShutDown | Write | Boolean | Enabling this policy hides shut down/update and shut down from appearing in the power button in the start menu. | - |
| StartMenuHideSignOut | Write | Boolean | Enabling this policy hides sign out from appearing in the user tile in the start menu. | - |
| StartMenuHideSleep | Write | Boolean | Enabling this policy hides sleep from appearing in the power button in the start menu. | - |
| StartMenuHideSwitchAccount | Write | Boolean | Enabling this policy hides switch account from appearing in the user tile in the start menu. | - |
| StartMenuHideUserTile | Write | Boolean | Enabling this policy hides the user tile from appearing in the start menu. | - |
| StartMenuLayoutEdgeAssetsXml | Write | String | This policy setting allows you to import Edge assets to be used with startMenuLayoutXml policy. Start layout can contain secondary tile from Edge app which looks for Edge local asset file. Edge local asset would not exist and cause Edge secondary tile to appear empty in this case. This policy only gets applied when startMenuLayoutXml policy is modified. The value should be a UTF-8 Base64 encoded byte array. | - |
| StartMenuLayoutXml | Write | String | Allows admins to override the default Start menu layout and prevents the user from changing it. The layout is modified by specifying an XML file based on a layout modification schema. XML needs to be in a UTF8 encoded byte array format. | - |
| StartMenuMode | Write | String | Allows admins to decide how the Start menu is displayed. Possible values are: userDefined, fullScreen, nonFullScreen. | `userDefined`, `fullScreen`, `nonFullScreen` |
| StartMenuPinnedFolderDocuments | Write | String | Enforces the visibility \(Show/Hide\) of the Documents folder shortcut on the Start menu. Possible values are: notConfigured, hide, show. | `notConfigured`, `hide`, `show` |
| StartMenuPinnedFolderDownloads | Write | String | Enforces the visibility \(Show/Hide\) of the Downloads folder shortcut on the Start menu. Possible values are: notConfigured, hide, show. | `notConfigured`, `hide`, `show` |
| StartMenuPinnedFolderFileExplorer | Write | String | Enforces the visibility \(Show/Hide\) of the FileExplorer shortcut on the Start menu. Possible values are: notConfigured, hide, show. | `notConfigured`, `hide`, `show` |
| StartMenuPinnedFolderHomeGroup | Write | String | Enforces the visibility \(Show/Hide\) of the HomeGroup folder shortcut on the Start menu. Possible values are: notConfigured, hide, show. | `notConfigured`, `hide`, `show` |
| StartMenuPinnedFolderMusic | Write | String | Enforces the visibility \(Show/Hide\) of the Music folder shortcut on the Start menu. Possible values are: notConfigured, hide, show. | `notConfigured`, `hide`, `show` |
| StartMenuPinnedFolderNetwork | Write | String | Enforces the visibility \(Show/Hide\) of the Network folder shortcut on the Start menu. Possible values are: notConfigured, hide, show. | `notConfigured`, `hide`, `show` |
| StartMenuPinnedFolderPersonalFolder | Write | String | Enforces the visibility \(Show/Hide\) of the PersonalFolder shortcut on the Start menu. Possible values are: notConfigured, hide, show. | `notConfigured`, `hide`, `show` |
| StartMenuPinnedFolderPictures | Write | String | Enforces the visibility \(Show/Hide\) of the Pictures folder shortcut on the Start menu. Possible values are: notConfigured, hide, show. | `notConfigured`, `hide`, `show` |
| StartMenuPinnedFolderSettings | Write | String | Enforces the visibility \(Show/Hide\) of the Settings folder shortcut on the Start menu. Possible values are: notConfigured, hide, show. | `notConfigured`, `hide`, `show` |
| StartMenuPinnedFolderVideos | Write | String | Enforces the visibility \(Show/Hide\) of the Videos folder shortcut on the Start menu. Possible values are: notConfigured, hide, show. | `notConfigured`, `hide`, `show` |
| StorageBlockRemovableStorage | Write | Boolean | Indicates whether or not to Block the user from using removable storage. | - |
| StorageRequireMobileDeviceEncryption | Write | Boolean | Indicating whether or not to require encryption on a mobile device. | - |
| StorageRestrictAppDataToSystemVolume | Write | Boolean | Indicates whether application data is restricted to the system drive. | - |
| StorageRestrictAppInstallToSystemVolume | Write | Boolean | Indicates whether the installation of applications is restricted to the system drive. | - |
| SystemTelemetryProxyServer | Write | String | Gets or sets the fully qualified domain name \(FQDN\) or IP address of a proxy server to forward Connected User Experiences and Telemetry requests. | - |
| TaskManagerBlockEndTask | Write | Boolean | Specify whether non-administrators can use Task Manager to end tasks. | - |
| TenantLockdownRequireNetworkDuringOutOfBoxExperience | Write | Boolean | Whether the device is required to connect to the network. | - |
| UninstallBuiltInApps | Write | Boolean | Indicates whether or not to uninstall a fixed list of built-in Windows apps. | - |
| UsbBlocked | Write | Boolean | Indicates whether or not to Block the user from USB connection. | - |
| VoiceRecordingBlocked | Write | Boolean | Indicates whether or not to Block the user from voice recording. | - |
| WebRtcBlockLocalhostIpAddress | Write | Boolean | Indicates whether or not user's localhost IP address is displayed while making phone calls using the WebRTC | - |
| WiFiBlockAutomaticConnectHotspots | Write | Boolean | Indicating whether or not to block automatically connecting to Wi-Fi hotspots. Has no impact if Wi-Fi is blocked. | - |
| WiFiBlocked | Write | Boolean | Indicates whether or not to Block the user from using Wi-Fi. | - |
| WiFiBlockManualConfiguration | Write | Boolean | Indicates whether or not to Block the user from using Wi-Fi manual configuration. | - |
| WiFiScanInterval | Write | UInt32 | Specify how often devices scan for Wi-Fi networks. Supported values are 1-500, where 100 = default, and 500 = low frequency. Valid values 1 to 500 | - |
| Windows10AppsForceUpdateSchedule | Write | MSFT\_MicrosoftGraphwindows10AppsForceUpdateSchedule | Windows 10 force update schedule for Apps. | - |
| WindowsSpotlightBlockConsumerSpecificFeatures | Write | Boolean | Allows IT admins to block experiences that are typically for consumers only, such as Start suggestions, Membership notifications, Post-OOBE app install and redirect tiles. | - |
| WindowsSpotlightBlocked | Write | Boolean | Allows IT admins to turn off all Windows Spotlight features | - |
| WindowsSpotlightBlockOnActionCenter | Write | Boolean | Block suggestions from Microsoft that show after each OS clean install, upgrade or in an on-going basis to introduce users to what is new or changed | - |
| WindowsSpotlightBlockTailoredExperiences | Write | Boolean | Block personalized content in Windows spotlight based on users device usage. | - |
| WindowsSpotlightBlockThirdPartyNotifications | Write | Boolean | Block third party content delivered via Windows Spotlight | - |
| WindowsSpotlightBlockWelcomeExperience | Write | Boolean | Block Windows Spotlight Windows welcome experience | - |
| WindowsSpotlightBlockWindowsTips | Write | Boolean | Allows IT admins to turn off the popup of Windows Tips. | - |
| WindowsSpotlightConfigureOnLockScreen | Write | String | Specifies the type of Spotlight. Possible values are: notConfigured, disabled, enabled. | `notConfigured`, `disabled`, `enabled` |
| WindowsStoreBlockAutoUpdate | Write | Boolean | Indicates whether or not to block automatic update of apps from Windows Store. | - |
| WindowsStoreBlocked | Write | Boolean | Indicates whether or not to Block the user from using the Windows store. | - |
| WindowsStoreEnablePrivateStoreOnly | Write | Boolean | Indicates whether or not to enable Private Store Only. | - |
| WirelessDisplayBlockProjectionToThisDevice | Write | Boolean | Indicates whether or not to allow other devices from discovering this PC for projection. | - |
| WirelessDisplayBlockUserInputFromReceiver | Write | Boolean | Indicates whether or not to allow user input from wireless display receiver. | - |
| WirelessDisplayRequirePinForPairing | Write | Boolean | Indicates whether or not to require a PIN for new devices to initiate pairing. | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| SupportsScopeTags | Write | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphDefenderDetectedMalwareActions1

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| HighSeverity | Write | String | Indicates a Defender action to take for high severity Malware threat detected. Possible values are: deviceDefault, clean, quarantine, remove, allow, userDefined, block. | `deviceDefault`, `clean`, `quarantine`, `remove`, `allow`, `userDefined`, `block` |
| LowSeverity | Write | String | Indicates a Defender action to take for low severity Malware threat detected. Possible values are: deviceDefault, clean, quarantine, remove, allow, userDefined, block. | `deviceDefault`, `clean`, `quarantine`, `remove`, `allow`, `userDefined`, `block` |
| ModerateSeverity | Write | String | Indicates a Defender action to take for moderate severity Malware threat detected. Possible values are: deviceDefault, clean, quarantine, remove, allow, userDefined, block. | `deviceDefault`, `clean`, `quarantine`, `remove`, `allow`, `userDefined`, `block` |
| SevereSeverity | Write | String | Indicates a Defender action to take for severe severity Malware threat detected. Possible values are: deviceDefault, clean, quarantine, remove, allow, userDefined, block. | `deviceDefault`, `clean`, `quarantine`, `remove`, `allow`, `userDefined`, `block` |

#### MSFT\_MicrosoftGraphEdgeHomeButtonConfiguration

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| HomeButtonCustomURL | Write | String | The specific URL to load. | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.edgeHomeButtonHidden`, `#microsoft.graph.edgeHomeButtonLoadsStartPage`, `#microsoft.graph.edgeHomeButtonOpensCustomURL`, `#microsoft.graph.edgeHomeButtonOpensNewTab` |

#### MSFT\_MicrosoftGraphEdgeSearchEngineBase

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| EdgeSearchEngineType | Write | String | Allows IT admins to set a predefined default search engine for MDM-Controlled devices. Possible values are: default, bing. | `default`, `bing` |
| EdgeSearchEngineOpenSearchXmlUrl | Write | String | Points to a https link containing the OpenSearch xml file that contains, at minimum, the short name and the URL to the search Engine. | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.edgeSearchEngine`, `#microsoft.graph.edgeSearchEngineCustom` |

#### MSFT\_MicrosoftGraphWindows10NetworkProxyServer

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Address | Write | String | Address to the proxy server. Specify an address in the format ':' | - |
| Exceptions | Write | StringArray\[\] | Addresses that should not use the proxy server. The system will not use the proxy server for addresses beginning with what is specified in this node. | - |
| UseForLocalAddresses | Write | Boolean | Specifies whether the proxy server should be used for local \(intranet\) addresses. | - |

#### MSFT\_MicrosoftGraphWindows10AppsForceUpdateSchedule

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Recurrence | Write | String | Recurrence schedule. Possible values are: none, daily, weekly, monthly. | `none`, `daily`, `weekly`, `monthly` |
| RunImmediatelyIfAfterStartDateTime | Write | Boolean | If true, runs the task immediately if StartDateTime is in the past, else, runs at the next recurrence. | - |
| StartDateTime | Write | String | The start time for the force restart. | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationScepCertificatePolicyWindows10 resource type

### Description

Intune Device Configuration Scep Certificate Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| CertificateStore | Write | String | Target store certificate. Possible values are: user, machine. | `user`, `machine` |
| HashAlgorithm | Write | String | SCEP Hash Algorithm. Possible values are: sha1, sha2. | `sha1`, `sha2` |
| KeySize | Write | String | SCEP Key Size. Possible values are: size1024, size2048, size4096. | `size1024`, `size2048`, `size4096` |
| KeyUsage | Write | StringArray\[\] | SCEP Key Usage. Possible values are: keyEncipherment, digitalSignature. | `keyEncipherment`, `digitalSignature` |
| ScepServerUrls | Write | StringArray\[\] | SCEP Server Url\(s\). | - |
| SubjectAlternativeNameFormatString | Write | String | Custom String that defines the AAD Attribute. | - |
| SubjectNameFormatString | Write | String | Custom format to use with SubjectNameFormat = Custom. Example: CN={{UserName}},E={{EmailAddress}},OU=Enterprise Users,O=Contoso Corporation,L=Redmond,ST=WA,C=US | - |
| CustomSubjectAlternativeNames | Write | MSFT\_MicrosoftGraphcustomSubjectAlternativeName\[\] | Custom Subject Alternative Name Settings. This collection can contain a maximum of 500 elements. | - |
| ExtendedKeyUsages | Write | MSFT\_MicrosoftGraphextendedKeyUsage\[\] | Extended Key Usage \(EKU\) settings. This collection can contain a maximum of 500 elements. | - |
| CertificateValidityPeriodScale | Write | String | Scale for the Certificate Validity Period. Possible values are: days, months, years. | `days`, `months`, `years` |
| CertificateValidityPeriodValue | Write | UInt32 | Value for the Certificate Validity Period | - |
| KeyStorageProvider | Write | String | Key Storage Provider \(KSP\). Possible values are: useTpmKspOtherwiseUseSoftwareKsp, useTpmKspOtherwiseFail, usePassportForWorkKspOtherwiseFail, useSoftwareKsp. | `useTpmKspOtherwiseUseSoftwareKsp`, `useTpmKspOtherwiseFail`, `usePassportForWorkKspOtherwiseFail`, `useSoftwareKsp` |
| RenewalThresholdPercentage | Write | UInt32 | Certificate renewal threshold percentage. Valid values 1 to 99 | - |
| SubjectAlternativeNameType | Write | String | Certificate Subject Alternative Name Type. Possible values are: none, emailAddress, userPrincipalName, customAzureADAttribute, domainNameService, universalResourceIdentifier. | `none`, `emailAddress`, `userPrincipalName`, `customAzureADAttribute`, `domainNameService`, `universalResourceIdentifier` |
| SubjectNameFormat | Write | String | Certificate Subject Name Format. Possible values are: commonName, commonNameIncludingEmail, commonNameAsEmail, custom, commonNameAsIMEI, commonNameAsSerialNumber, commonNameAsAadDeviceId, commonNameAsIntuneDeviceId, commonNameAsDurableDeviceId. | `commonName`, `commonNameIncludingEmail`, `commonNameAsEmail`, `custom`, `commonNameAsIMEI`, `commonNameAsSerialNumber`, `commonNameAsAadDeviceId`, `commonNameAsIntuneDeviceId`, `commonNameAsDurableDeviceId` |
| RootCertificateDisplayName | Write | String | Trusted Root Certificate DisplayName | - |
| RootCertificateId | Write | String | Trusted Root Certificate Id | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphCustomSubjectAlternativeName

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Write | String | Custom SAN Name | - |
| SanType | Write | String | Custom SAN Type. Possible values are: none, emailAddress, userPrincipalName, customAzureADAttribute, domainNameService, universalResourceIdentifier. | `none`, `emailAddress`, `userPrincipalName`, `customAzureADAttribute`, `domainNameService`, `universalResourceIdentifier` |

#### MSFT\_MicrosoftGraphExtendedKeyUsage

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Write | String | Extended Key Usage Name | - |
| ObjectIdentifier | Write | String | Extended Key Usage Object Identifier | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationSecureAssessmentPolicyWindows10 resource type

### Description

Intune Device Configuration Secure Assessment Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AllowPrinting | Write | Boolean | Indicates whether or not to allow the app from printing during the test. | - |
| AllowScreenCapture | Write | Boolean | Indicates whether or not to allow screen capture capability during a test. | - |
| AllowTextSuggestion | Write | Boolean | Indicates whether or not to allow text suggestions during the test. | - |
| AssessmentAppUserModelId | Write | String | Specifies the application user model ID of the assessment app launched when a user signs in to a secure assessment with a local guest account. Important notice: this property must be set with localGuestAccountName in order to make the local guest account sign-in experience work properly for secure assessments. | - |
| ConfigurationAccount | Write | String | The account used to configure the Windows device for taking the test. The user can be a domain account \(domain/user\), an AAD account \(usernametenant.com\) or a local account \(username\). | - |
| ConfigurationAccountType | Write | String | The account type used to by ConfigurationAccount. Possible values are: azureADAccount, domainAccount, localAccount, localGuestAccount. | `azureADAccount`, `domainAccount`, `localAccount`, `localGuestAccount` |
| LaunchUri | Write | String | Url link to an assessment that's automatically loaded when the secure assessment browser is launched. It has to be a valid Url \([https://msdn.microsoft.com/](https://msdn.microsoft.com/)\). | - |
| LocalGuestAccountName | Write | String | Specifies the display text for the local guest account shown on the sign-in screen. Typically is the name of an assessment. When the user clicks the local guest account on the sign-in screen, an assessment app is launched with a specified assessment URL. Secure assessments can only be configured with local guest account sign-in on devices running Windows 10, version 1903 or later. Important notice: this property must be set with assessmentAppUserModelID in order to make the local guest account sign-in experience work properly for secure assessments. | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationSharedMultiDevicePolicyWindows10 resource type

### Description

Intune Device Configuration Shared Multi Device Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AccountManagerPolicy | Write | MSFT\_MicrosoftGraphsharedPCAccountManagerPolicy | Specifies how accounts are managed on a shared PC. Only applies when disableAccountManager is false. | - |
| AllowedAccounts | Write | StringArray\[\] | Indicates which type of accounts are allowed to use on a shared PC. Possible values are: notConfigured, guest, domain. | `notConfigured`, `guest`, `domain` |
| AllowLocalStorage | Write | Boolean | Specifies whether local storage is allowed on a shared PC. | - |
| DisableAccountManager | Write | Boolean | Disables the account manager for shared PC mode. | - |
| DisableEduPolicies | Write | Boolean | Specifies whether the default shared PC education environment policies should be disabled. For Windows 10 RS2 and later, this policy will be applied without setting Enabled to true. | - |
| DisablePowerPolicies | Write | Boolean | Specifies whether the default shared PC power policies should be disabled. | - |
| DisableSignInOnResume | Write | Boolean | Disables the requirement to sign in whenever the device wakes up from sleep mode. | - |
| Enabled | Write | Boolean | Enables shared PC mode and applies the shared pc policies. | - |
| FastFirstSignIn | Write | String | Specifies whether to auto connect new non-admin Microsoft Entra accounts to pre-configured candidate local accounts. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| IdleTimeBeforeSleepInSeconds | Write | UInt32 | Specifies the time in seconds that a device must sit idle before the PC goes to sleep. Setting this value to 0 prevents the sleep timeout from occurring. | - |
| KioskAppDisplayName | Write | String | Specifies the display text for the account shown on the sign-in screen which launches the app specified by SetKioskAppUserModelId. Only applies when KioskAppUserModelId is set. | - |
| KioskAppUserModelId | Write | String | Specifies the application user model ID of the app to use with assigned access. | - |
| LocalStorage | Write | String | Specifies whether local storage is allowed on a shared PC. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| MaintenanceStartTime | Write | String | Specifies the daily start time of maintenance hour. | - |
| SetAccountManager | Write | String | Disables the account manager for shared PC mode. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| SetEduPolicies | Write | String | Specifies whether the default shared PC education environment policies should be enabled/disabled/not configured. For Windows 10 RS2 and later, this policy will be applied without setting Enabled to true. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| SetPowerPolicies | Write | String | Specifies whether the default shared PC power policies should be enabled/disabled. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| SignInOnResume | Write | String | Specifies the requirement to sign in whenever the device wakes up from sleep mode. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphSharedPCAccountManagerPolicy

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AccountDeletionPolicy | Write | String | Configures when accounts are deleted. Possible values are: immediate, diskSpaceThreshold, diskSpaceThresholdOrInactiveThreshold. | `immediate`, `diskSpaceThreshold`, `diskSpaceThresholdOrInactiveThreshold` |
| CacheAccountsAboveDiskFreePercentage | Write | UInt32 | Sets the percentage of available disk space a PC should have before it stops deleting cached shared PC accounts. Only applies when AccountDeletionPolicy is DiskSpaceThreshold or DiskSpaceThresholdOrInactiveThreshold. Valid values 0 to 100 | - |
| InactiveThresholdDays | Write | UInt32 | Specifies when the accounts will start being deleted when they have not been logged on during the specified period, given as number of days. Only applies when AccountDeletionPolicy is DiskSpaceThreshold or DiskSpaceThresholdOrInactiveThreshold. | - |
| RemoveAccountsBelowDiskFreePercentage | Write | UInt32 | Sets the percentage of disk space remaining on a PC before cached accounts will be deleted to free disk space. Accounts that have been inactive the longest will be deleted first. Only applies when AccountDeletionPolicy is DiskSpaceThresholdOrInactiveThreshold. Valid values 0 to 100 | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationTrustedCertificatePolicyWindows10 resource type

### Description

Intune Device Configuration Trusted Certificate Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| CertFileName | Write | String | File name to display in UI. | - |
| DestinationStore | Write | String | Destination store location for the Trusted Root Certificate. Possible values are: computerCertStoreRoot, computerCertStoreIntermediate, userCertStoreIntermediate. | `computerCertStoreRoot`, `computerCertStoreIntermediate`, `userCertStoreIntermediate` |
| TrustedRootCertificate | Write | String | Trusted Root Certificate | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationVpnPolicyWindows10 resource type

### Description

Intune Device Configuration Vpn Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AssociatedApps | Write | MSFT\_MicrosoftGraphwindows10AssociatedApps\[\] | Associated Apps. This collection can contain a maximum of 10000 elements. | - |
| AuthenticationMethod | Write | String | Authentication method. Possible values are: certificate, usernameAndPassword, customEapXml, derivedCredential. | `certificate`, `usernameAndPassword`, `customEapXml`, `derivedCredential` |
| ConnectionType | Write | String | Connection type. Possible values are: pulseSecure, f5EdgeClient, dellSonicWallMobileConnect, checkPointCapsuleVpn, automatic, ikEv2, l2tp, pptp, citrix, paloAltoGlobalProtect, ciscoAnyConnect, unknownFutureValue, microsoftTunnel. | `pulseSecure`, `f5EdgeClient`, `dellSonicWallMobileConnect`, `checkPointCapsuleVpn`, `automatic`, `ikEv2`, `l2tp`, `pptp`, `citrix`, `paloAltoGlobalProtect`, `ciscoAnyConnect`, `unknownFutureValue`, `microsoftTunnel` |
| CryptographySuite | Write | MSFT\_MicrosoftGraphcryptographySuite | Cryptography Suite security settings for IKEv2 VPN in Windows10 and above | - |
| DnsRules | Write | MSFT\_MicrosoftGraphvpnDnsRule\[\] | DNS rules. This collection can contain a maximum of 1000 elements. | - |
| DnsSuffixes | Write | StringArray\[\] | Specify DNS suffixes to add to the DNS search list to properly route short names. | - |
| EapXml | Write | String | Extensible Authentication Protocol \(EAP\) XML. \(UTF8 encoded byte array\) | - |
| EnableAlwaysOn | Write | Boolean | Enable Always On mode. | - |
| EnableConditionalAccess | Write | Boolean | Enable conditional access. | - |
| EnableDeviceTunnel | Write | Boolean | Enable device tunnel. | - |
| EnableDnsRegistration | Write | Boolean | Enable IP address registration with internal DNS. | - |
| EnableSingleSignOnWithAlternateCertificate | Write | Boolean | Enable single sign-on \(SSO\) with alternate certificate. | - |
| EnableSplitTunneling | Write | Boolean | Enable split tunneling. | - |
| MicrosoftTunnelSiteId | Write | String | ID of the Microsoft Tunnel site associated with the VPN profile. | - |
| OnlyAssociatedAppsCanUseConnection | Write | Boolean | Only associated Apps can use connection \(per-app VPN\). | - |
| ProfileTarget | Write | String | Profile target type. Possible values are: user, device, autoPilotDevice. | `user`, `device`, `autoPilotDevice` |
| ProxyServer | Write | MSFT\_MicrosoftGraphwindows10VpnProxyServer | Proxy Server. | - |
| RememberUserCredentials | Write | Boolean | Remember user credentials. | - |
| Routes | Write | MSFT\_MicrosoftGraphvpnRoute\[\] | Routes \(optional for third-party providers\). This collection can contain a maximum of 1000 elements. | - |
| SingleSignOnEku | Write | MSFT\_MicrosoftGraphextendedKeyUsage | Single sign-on Extended Key Usage \(EKU\). | - |
| SingleSignOnIssuerHash | Write | String | Single sign-on issuer hash. | - |
| TrafficRules | Write | MSFT\_MicrosoftGraphvpnTrafficRule\[\] | Traffic rules. This collection can contain a maximum of 1000 elements. | - |
| TrustedNetworkDomains | Write | StringArray\[\] | Trusted Network Domains | - |
| WindowsInformationProtectionDomain | Write | String | Windows Information Protection \(WIP\) domain to associate with this connection. | - |
| ConnectionName | Write | String | Connection name displayed to the user. | - |
| CustomXml | Write | String | Custom XML commands that configures the VPN connection. \(UTF8 encoded byte array\) | - |
| ServerCollection | Write | MSFT\_MicrosoftGraphvpnServer\[\] | List of VPN Servers on the network. Make sure end users can access these network locations. This collection can contain a maximum of 500 elements. | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphWindows10AssociatedApps

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AppType | Write | String | Application type. Possible values are: desktop, universal. | `desktop`, `universal` |
| Identifier | Write | String | Identifier. | - |

#### MSFT\_MicrosoftGraphCryptographySuite

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AuthenticationTransformConstants | Write | String | Authentication Transform Constants. Possible values are: md5\_96, sha1\_96, sha\_256\_128, aes128Gcm, aes192Gcm, aes256Gcm. | `md5_96`, `sha1_96`, `sha_256_128`, `aes128Gcm`, `aes192Gcm`, `aes256Gcm` |
| CipherTransformConstants | Write | String | Cipher Transform Constants. Possible values are: aes256, des, tripleDes, aes128, aes128Gcm, aes256Gcm, aes192, aes192Gcm, chaCha20Poly1305. | `aes256`, `des`, `tripleDes`, `aes128`, `aes128Gcm`, `aes256Gcm`, `aes192`, `aes192Gcm`, `chaCha20Poly1305` |
| DhGroup | Write | String | Diffie Hellman Group. Possible values are: group1, group2, group14, ecp256, ecp384, group24. | `group1`, `group2`, `group14`, `ecp256`, `ecp384`, `group24` |
| EncryptionMethod | Write | String | Encryption Method. Possible values are: aes256, des, tripleDes, aes128, aes128Gcm, aes256Gcm, aes192, aes192Gcm, chaCha20Poly1305. | `aes256`, `des`, `tripleDes`, `aes128`, `aes128Gcm`, `aes256Gcm`, `aes192`, `aes192Gcm`, `chaCha20Poly1305` |
| IntegrityCheckMethod | Write | String | Integrity Check Method. Possible values are: sha2\_256, sha1\_96, sha1\_160, sha2\_384, sha2\_512, md5. | `sha2_256`, `sha1_96`, `sha1_160`, `sha2_384`, `sha2_512`, `md5` |
| PfsGroup | Write | String | Perfect Forward Secrecy Group. Possible values are: pfs1, pfs2, pfs2048, ecp256, ecp384, pfsMM, pfs24. | `pfs1`, `pfs2`, `pfs2048`, `ecp256`, `ecp384`, `pfsMM`, `pfs24` |

#### MSFT\_MicrosoftGraphVpnDnsRule

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AutoTrigger | Write | Boolean | Automatically connect to the VPN when the device connects to this domain: Default False. | - |
| Name | Write | String | Name. | - |
| Persistent | Write | Boolean | Keep this rule active even when the VPN is not connected: Default False | - |
| ProxyServerUri | Write | String | Proxy Server Uri. | - |
| Servers | Write | StringArray\[\] | Servers. | - |

#### MSFT\_MicrosoftGraphWindows10VpnProxyServer

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| BypassProxyServerForLocalAddress | Write | Boolean | Bypass proxy server for local address. | - |
| Address | Write | String | Address. | - |
| AutomaticConfigurationScriptUrl | Write | String | Proxy's automatic configuration script url. | - |
| Port | Write | UInt32 | Port. Valid values 0 to 65535 | - |
| AutomaticallyDetectProxySettings | Write | Boolean | Automatically detect proxy settings. | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.windows10VpnProxyServer`, `#microsoft.graph.windows81VpnProxyServer` |

#### MSFT\_MicrosoftGraphVpnRoute

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DestinationPrefix | Write | String | Destination prefix \(IPv4/v6 address\). | - |
| PrefixSize | Write | UInt32 | Prefix size. \(1-32\). Valid values 1 to 32 | - |

#### MSFT\_MicrosoftGraphExtendedKeyUsage

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Write | String | Extended Key Usage Name | - |
| ObjectIdentifier | Write | String | Extended Key Usage Object Identifier | - |

#### MSFT\_MicrosoftGraphVpnTrafficRule

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AppId | Write | String | App identifier, if this traffic rule is triggered by an app. | - |
| AppType | Write | String | App type, if this traffic rule is triggered by an app. Possible values are: none, desktop, universal. | `none`, `desktop`, `universal` |
| Claims | Write | String | Claims associated with this traffic rule. | - |
| LocalAddressRanges | Write | MSFT\_MicrosoftGraphIPv4Range\[\] | Local address range. This collection can contain a maximum of 500 elements. | - |
| LocalPortRanges | Write | MSFT\_MicrosoftGraphNumberRange\[\] | Local port range can be set only when protocol is either TCP or UDP \(6 or 17\). This collection can contain a maximum of 500 elements. | - |
| Name | Write | String | Name. | - |
| Protocols | Write | UInt32 | Protocols \(0-255\). Valid values 0 to 255 | - |
| RemoteAddressRanges | Write | MSFT\_MicrosoftGraphIPv4Range\[\] | Remote address range. This collection can contain a maximum of 500 elements. | - |
| RemotePortRanges | Write | MSFT\_MicrosoftGraphNumberRange\[\] | Remote port range can be set only when protocol is either TCP or UDP \(6 or 17\). This collection can contain a maximum of 500 elements. | - |
| RoutingPolicyType | Write | String | When app triggered, indicates whether to enable split tunneling along this route. Possible values are: none, splitTunnel, forceTunnel. | `none`, `splitTunnel`, `forceTunnel` |
| VpnTrafficDirection | Write | String | Specify whether the rule applies to inbound traffic or outbound traffic. Possible values are: outbound, inbound, unknownFutureValue. | `outbound`, `inbound`, `unknownFutureValue` |

#### MSFT\_MicrosoftGraphIPv4Range

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| LowerAddress | Write | String | Lower address. | - |
| UpperAddress | Write | String | Upper address. | - |
| CidrAddress | Write | String | IPv4 address in CIDR notation. Not nullable. | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.iPv4CidrRange`, `#microsoft.graph.iPv6CidrRange`, `#microsoft.graph.iPv4Range`, `#microsoft.graph.iPv6Range` |

#### MSFT\_MicrosoftGraphNumberRange

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| LowerNumber | Write | UInt32 | Lower number. | - |
| UpperNumber | Write | UInt32 | Upper number. | - |

#### MSFT\_MicrosoftGraphVpnServer

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Address | Write | String | Address \(IP address, FQDN or URL\) | - |
| Description | Write | String | Description. | - |
| IsDefaultServer | Write | Boolean | Default server. | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationWindowsTeamPolicyWindows10 resource type

### Description

Intune Device Configuration Windows Team Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AzureOperationalInsightsBlockTelemetry | Write | Boolean | Indicates whether or not to Block Azure Operational Insights. | - |
| AzureOperationalInsightsWorkspaceId | Write | String | The Azure Operational Insights workspace id. | - |
| AzureOperationalInsightsWorkspaceKey | Write | String | The Azure Operational Insights Workspace key. | - |
| ConnectAppBlockAutoLaunch | Write | Boolean | Specifies whether to automatically launch the Connect app whenever a projection is initiated. | - |
| MaintenanceWindowBlocked | Write | Boolean | Indicates whether or not to Block setting a maintenance window for device updates. | - |
| MaintenanceWindowDurationInHours | Write | UInt32 | Maintenance window duration for device updates. Valid values 0 to 5 | - |
| MaintenanceWindowStartTime | Write | String | Maintenance window start time for device updates. | - |
| MiracastBlocked | Write | Boolean | Indicates whether or not to Block wireless projection. | - |
| MiracastChannel | Write | String | The channel. Possible values are: userDefined, one, two, three, four, five, six, seven, eight, nine, ten, eleven, thirtySix, forty, fortyFour, fortyEight, oneHundredFortyNine, oneHundredFiftyThree, oneHundredFiftySeven, oneHundredSixtyOne, oneHundredSixtyFive. | `userDefined`, `one`, `two`, `three`, `four`, `five`, `six`, `seven`, `eight`, `nine`, `ten`, `eleven`, `thirtySix`, `forty`, `fortyFour`, `fortyEight`, `oneHundredFortyNine`, `oneHundredFiftyThree`, `oneHundredFiftySeven`, `oneHundredSixtyOne`, `oneHundredSixtyFive` |
| MiracastRequirePin | Write | Boolean | Indicates whether or not to require a pin for wireless projection. | - |
| SettingsBlockMyMeetingsAndFiles | Write | Boolean | Specifies whether to disable the 'My meetings and files' feature in the Start menu, which shows the signed-in user's meetings and files from Office 365. | - |
| SettingsBlockSessionResume | Write | Boolean | Specifies whether to allow the ability to resume a session when the session times out. | - |
| SettingsBlockSigninSuggestions | Write | Boolean | Specifies whether to disable auto-populating of the sign-in dialog with invitees from scheduled meetings. | - |
| SettingsDefaultVolume | Write | UInt32 | Specifies the default volume value for a new session. Permitted values are 0-100. The default is 45. Valid values 0 to 100 | - |
| SettingsScreenTimeoutInMinutes | Write | UInt32 | Specifies the number of minutes until the Hub screen turns off. | - |
| SettingsSessionTimeoutInMinutes | Write | UInt32 | Specifies the number of minutes until the session times out. | - |
| SettingsSleepTimeoutInMinutes | Write | UInt32 | Specifies the number of minutes until the Hub enters sleep mode. | - |
| WelcomeScreenBackgroundImageUrl | Write | String | The welcome screen background image URL. The URL must use the HTTPS protocol and return a PNG image. | - |
| WelcomeScreenBlockAutomaticWakeUp | Write | Boolean | Indicates whether or not to Block the welcome screen from waking up automatically when someone enters the room. | - |
| WelcomeScreenMeetingInformation | Write | String | The welcome screen meeting information shown. Possible values are: userDefined, showOrganizerAndTimeOnly, showOrganizerAndTimeAndSubject. | `userDefined`, `showOrganizerAndTimeOnly`, `showOrganizerAndTimeAndSubject` |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| SupportsScopeTags | Write | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceConfigurationWiredNetworkPolicyWindows10 resource type

### Description

Intune Device Configuration Wired Network Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AuthenticationBlockPeriodInMinutes | Write | UInt32 | Specify the duration for which automatic authentication attempts will be blocked from occuring after a failed authentication attempt. | - |
| AuthenticationMethod | Write | String | Specify the authentication method. Possible values are: certificate, usernameAndPassword, derivedCredential. Possible values are: certificate, usernameAndPassword, derivedCredential, unknownFutureValue. | `certificate`, `usernameAndPassword`, `derivedCredential`, `unknownFutureValue` |
| AuthenticationPeriodInSeconds | Write | UInt32 | Specify the number of seconds for the client to wait after an authentication attempt before failing. Valid range 1-3600. | - |
| AuthenticationRetryDelayPeriodInSeconds | Write | UInt32 | Specify the number of seconds between a failed authentication and the next authentication attempt. Valid range 1-3600. | - |
| AuthenticationType | Write | String | Specify whether to authenticate the user, the device, either, or to use guest authentication \(none\). If you're using certificate authentication, make sure the certificate type matches the authentication type. Possible values are: none, user, machine, machineOrUser, guest. Possible values are: none, user, machine, machineOrUser, guest, unknownFutureValue. | `none`, `user`, `machine`, `machineOrUser`, `guest`, `unknownFutureValue` |
| CacheCredentials | Write | Boolean | When TRUE, caches user credentials on the device so that users don't need to keep entering them each time they connect. When FALSE, do not cache credentials. Default value is FALSE. | - |
| DisableUserPromptForServerValidation | Write | Boolean | When TRUE, prevents the user from being prompted to authorize new servers for trusted certification authorities when EAP type is selected as PEAP. When FALSE, does not prevent the user from being prompted. Default value is FALSE. | - |
| EapolStartPeriodInSeconds | Write | UInt32 | Specify the number of seconds to wait before sending an EAPOL \(Extensible Authentication Protocol over LAN\) Start message. Valid range 1-3600. | - |
| EapType | Write | String | Extensible Authentication Protocol \(EAP\). Indicates the type of EAP protocol set on the Wi-Fi endpoint \(router\). Possible values are: eapTls, leap, eapSim, eapTtls, peap, eapFast, teap. Possible values are: eapTls, leap, eapSim, eapTtls, peap, eapFast, teap. | `eapTls`, `leap`, `eapSim`, `eapTtls`, `peap`, `eapFast`, `teap` |
| Enforce8021X | Write | Boolean | When TRUE, the automatic configuration service for wired networks requires the use of 802.1X for port authentication. When FALSE, 802.1X is not required. Default value is FALSE. | - |
| ForceFIPSCompliance | Write | Boolean | When TRUE, forces FIPS compliance. When FALSE, does not enable FIPS compliance. Default value is FALSE. | - |
| InnerAuthenticationProtocolForEAPTTLS | Write | String | Specify inner authentication protocol for EAP TTLS. Possible values are: unencryptedPassword, challengeHandshakeAuthenticationProtocol, microsoftChap, microsoftChapVersionTwo. Possible values are: unencryptedPassword, challengeHandshakeAuthenticationProtocol, microsoftChap, microsoftChapVersionTwo. | `unencryptedPassword`, `challengeHandshakeAuthenticationProtocol`, `microsoftChap`, `microsoftChapVersionTwo` |
| MaximumAuthenticationFailures | Write | UInt32 | Specify the maximum authentication failures allowed for a set of credentials. Valid range 1-100. | - |
| MaximumEAPOLStartMessages | Write | UInt32 | Specify the maximum number of EAPOL \(Extensible Authentication Protocol over LAN\) Start messages to be sent before returning failure. Valid range 1-100. | - |
| OuterIdentityPrivacyTemporaryValue | Write | String | Specify the string to replace usernames for privacy when using EAP TTLS or PEAP. | - |
| PerformServerValidation | Write | Boolean | When TRUE, enables verification of server's identity by validating the certificate when EAP type is selected as PEAP. When FALSE, the certificate is not validated. Default value is TRUE. | - |
| RequireCryptographicBinding | Write | Boolean | When TRUE, enables cryptographic binding when EAP type is selected as PEAP. When FALSE, does not enable cryptogrpahic binding. Default value is TRUE. | - |
| SecondaryAuthenticationMethod | Write | String | Specify the secondary authentication method. Possible values are: certificate, usernameAndPassword, derivedCredential. Possible values are: certificate, usernameAndPassword, derivedCredential, unknownFutureValue. | `certificate`, `usernameAndPassword`, `derivedCredential`, `unknownFutureValue` |
| TrustedServerCertificateNames | Write | StringArray\[\] | Specify trusted server certificate names. | - |
| RootCertificatesForServerValidationIds | Write | StringArray\[\] | Specify root certificates for server validation. This collection can contain a maximum of 500 elements. | - |
| RootCertificatesForServerValidationDisplayNames | Write | StringArray\[\] | Specify root certificate display names for server validation. This collection can contain a maximum of 500 elements. | - |
| IdentityCertificateForClientAuthenticationId | Write | String | Specify identity certificate for client authentication. | - |
| IdentityCertificateForClientAuthenticationDisplayName | Write | String | Specify identity certificate display name for client authentication. | - |
| SecondaryIdentityCertificateForClientAuthenticationId | Write | String | Specify root certificate for client validation | - |
| SecondaryIdentityCertificateForClientAuthenticationDisplayName | Write | String | Specify root certificate display name for client validation | - |
| RootCertificateForClientValidationId | Write | String | Specify root certificate for client validation. | - |
| RootCertificateForClientValidationDisplayName | Write | String | Specify root certificate display name for client validation. | - |
| SecondaryRootCertificateForClientValidationId | Write | String | Specify secondary root certificate for client validation. | - |
| SecondaryRootCertificateForClientValidationDisplayName | Write | String | Specify secondary root certificate display name for client validation. | - |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## deviceEnrollmentLimitRestriction resource type

### Description

This resource configures the Intune device enrollment limit restrictions.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Display name of the device enrollment limit restriction. | - |
| Description | Write | String | Description of the device enrollment limit restriction. | - |
| Limit | Write | UInt32 | Specifies the maximum number of devices a user can enroll | - |
| Ensure | Write | String | Present ensures the restriction exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | DeviceManagementServiceConfig.Read.All |
| Update | DeviceManagementServiceConfig.ReadWrite.All |

## deviceEnrollmentPlatformRestriction resource type

### Description

This resource configures the Intune device platform enrollment restrictions.

**Be aware**: To deploy a Android platform restriction policy, two individual configurations must exist:

- The first one contains the key for `AndroidRestriction`
- The second one contains the key for `AndroidForWorkRestriction`

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the device enrollment platform restriction. | - |
| DisplayName | Key | String | Display name of the device enrollment platform restriction. | - |
| Description | Write | String | Description of the device enrollment platform restriction. | - |
| AndroidForWorkRestriction | Write | MSFT\_DeviceEnrollmentPlatformRestriction | Android for work restrictions based on platform, platform operating system version, and device ownership. | - |
| AndroidRestriction | Write | MSFT\_DeviceEnrollmentPlatformRestriction | Android restrictions based on platform, platform operating system version, and device ownership. | - |
| IosRestriction | Write | MSFT\_DeviceEnrollmentPlatformRestriction | Ios restrictions based on platform, platform operating system version, and device ownership. | - |
| MacOSRestriction | Write | MSFT\_DeviceEnrollmentPlatformRestriction | Mac restrictions based on platform, platform operating system version, and device ownership. | - |
| MacRestriction | Write | MSFT\_DeviceEnrollmentPlatformRestriction | Mac restrictions based on platform, platform operating system version, and device ownership. | - |
| WindowsHomeSkuRestriction | Write | MSFT\_DeviceEnrollmentPlatformRestriction | Windows Home Sku restrictions based on platform, platform operating system version, and device ownership. | - |
| WindowsMobileRestriction | Write | MSFT\_DeviceEnrollmentPlatformRestriction | Windows mobile restrictions based on platform, platform operating system version, and device ownership. | - |
| WindowsRestriction | Write | MSFT\_DeviceEnrollmentPlatformRestriction | Windows restrictions based on platform, platform operating system version, and device ownership. | - |
| DeviceEnrollmentConfigurationType | Write | String | Support for Enrollment Configuration Type | `platformRestrictions`, `singlePlatformRestriction` |
| Priority | Write | UInt32 | Priority is used when a user exists in multiple groups that are assigned enrollment configuration. Users are subject only to the configuration with the lowest priority value. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_DeviceEnrollmentPlatformRestriction

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| PlatformBlocked | Write | Boolean | Block the platform from enrolling. | - |
| PersonalDeviceEnrollmentBlocked | Write | Boolean | Block personally owned devices from enrolling. | - |
| OsMinimumVersion | Write | String | Min OS version supported. | - |
| OsMaximumVersion | Write | String | Max OS version supported. | - |
| BlockedManufacturers | Write | StringArray\[\] | Collection of blocked Manufacturers. | - |
| BlockedSkus | Write | StringArray\[\] | Collection of blocked Skus. | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementServiceConfig.Read.All |
| Update | Group.Read.All, DeviceManagementServiceConfig.ReadWrite.All |

## deviceEnrollmentStatusPageWindows10 resource type

### Description

Intune Device Enrollment Status Page Configuration for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | The display name of the device enrollment configuration | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Description | Write | String | The description of the device enrollment configuration | - |
| AllowDeviceResetOnInstallFailure | Write | Boolean | Allow or block device reset on installation failure | - |
| AllowDeviceUseOnInstallFailure | Write | Boolean | Allow the user to continue using the device on installation failure | - |
| AllowLogCollectionOnInstallFailure | Write | Boolean | Allow or block log collection on installation failure | - |
| AllowNonBlockingAppInstallation | Write | Boolean | Install all required apps as non blocking apps during white glove | - |
| BlockDeviceSetupRetryByUser | Write | Boolean | Allow the user to retry the setup on installation failure | - |
| CustomErrorMessage | Write | String | Set custom error message to show upon installation failure | - |
| DisableUserStatusTrackingAfterFirstUser | Write | Boolean | Only show installation progress for first user post enrollment | - |
| InstallProgressTimeoutInMinutes | Write | UInt32 | Set installation progress timeout in minutes | - |
| InstallQualityUpdates | Write | Boolean | Allows quality updates installation during OOBE | - |
| SelectedMobileAppIds | Write | StringArray\[\] | Ids of selected applications to track the installation status. When this parameter is used, SelectedMobileAppNames is ignored | - |
| SelectedMobileAppNames | Write | StringArray\[\] | Names of selected applications to track the installation status. This parameter is ignored when SelectedMobileAppIds is also specified | - |
| ShowInstallationProgress | Write | Boolean | Show or hide installation progress to user | - |
| TrackInstallProgressForAutopilotOnly | Write | Boolean | Only show installation progress for Autopilot enrollment scenarios | - |
| Priority | Write | UInt32 | Priority is used when a user exists in multiple groups that are assigned enrollment configuration. Users are subject only to the configuration with the lowest priority value. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All, DeviceManagementServiceConfig.Read.All, DeviceManagementApps.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All, DeviceManagementServiceConfig.ReadWrite.All, DeviceManagementApps.Read.All |

## endpointDetectionAndResponsePolicyWindows10 resource type

### Description

This resource configures an Intune Endpoint Detection and Response Policy for Windows 10.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Write | String | Identity of the endpoint detection and response policy for Windows 10. | - |
| DisplayName | Key | String | Display name of the endpoint detection and response policy for Windows 10. | - |
| Description | Write | String | Description of the endpoint detection and response policy for Windows 10. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the endpoint detection and response policy for Windows 10. | - |
| SampleSharing | Write | String | Return or set Windows Defender Advanced Threat Protection Sample Sharing configuration parameter: 0 - none, 1 - All | `0`, `1` |
| ConfigurationType | Write | String | Microsoft Defender for Endpoint endpoint detection and response capabilities provide advanced attack detections that are near real-time and actionable. Security analysts can prioritize alerts effectively, gain visibility into the full scope of a breach, and take response actions to remediate threats. | `AutoFromConnector`, `Onboard`, `Offboard` |
| ConfigurationBlob | Write | String | Set Windows Defender Advanced Threat Protection Onboarding blob and initiate onboarding to Windows Defender Advanced Threat Protection | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## exploitProtectionPolicyWindows10SettingCatalog resource type

### Description

This resource configures an Intune Endpoint Protection Exploit Protection policy for a Windows 10 Device. Enables the IT admin to push out a configuration representing the desired system and application mitigation options to all the devices in the organization. The configuration is represented by an XML. For more information Exploit Protection, see

- [Enable Exploit Protection on Devices and Import](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/enable-exploit-protection)
- [Export, and deploy Exploit Protection configurations](https://learn.microsoft.com/en-us/windows/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml)

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Write | String | Identity of the endpoint protection policy. | - |
| DisplayName | Key | String | Display name of the endpoint protection policy. | - |
| Description | Write | String | Description of the endpoint protection. | - |
| ExploitProtectionSettings | Write | String | Enables the IT admin to push out a configuration representing the desired system and application mitigation options to all the devices in the organization. The configuration is represented by an XML. | - |
| DisallowExploitProtectionOverride | Write | String | Prevent users from making changes to the exploit protection settings area in the Windows Defender Security Center.values 0:disable, 1:enable | `0`, `1` |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the endpoint protection. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## policySets resource type

### Description

Intune Policy Sets

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Description | Write | String | Description of the PolicySet. | - |
| DisplayName | Key | String | DisplayName of the PolicySet. | - |
| GuidedDeploymentTags | Write | StringArray\[\] | Tags of the guided deployment | - |
| RoleScopeTags | Write | StringArray\[\] | RoleScopeTags of the PolicySet | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Items | Write | MSFT\_DeviceManagementConfigurationPolicyItems\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_DeviceManagementConfigurationPolicyItems

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of policy the item represents. | - |
| payloadId | Write | String | The group Id of the policy the item represents. | - |
| displayName | Write | String | The collection display name of the policy the item represents | - |
| itemType | Write | String | The type of policy the item represents. | - |
| guidedDeploymentTags | Write | StringArray\[\] | Tags of the guided deployment | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## roleAssignment resource type

### Description

This resource configures an Intune Role Assignment.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The unique idenfier for an entity. Read-only. | - |
| Description | Write | String | Description of the Role Assignment. | - |
| DisplayName | Key | String | The display or friendly name of the role Assignment. | - |
| ResourceScopes | Write | StringArray\[\] | List of ids of role scope member security groups. These are IDs from Microsoft Entra. Ignored if ScopeType is not 'ResourceScope' | - |
| ResourceScopesDisplayNames | Write | StringArray\[\] | List of DisplayName of role scope member security groups. These are Displayname from Microsoft Entra. Ignored if ScopeType is not 'ResourceScope' | - |
| ScopeType | Write | String | Specifies the type of scope for a Role Assignment. Default type 'ResourceScope' allows assignment of ResourceScopes. Possible values are: resourceScope, allDevices, allLicensedUsers, allDevicesAndLicensedUsers. | - |
| Members | Write | StringArray\[\] | The list of ids of role member security groups. These are IDs from Microsoft Entra. | - |
| MembersDisplayNames | Write | StringArray\[\] | The list of Displaynames of role member security groups. These are Displaynamnes from Microsoft Entra. | - |
| RoleDefinition | Write | String | The Role Definition Id. | - |
| RoleDefinitionDisplayName | Write | String | The Role Definition Displayname. | - |
| Ensure | Write | String | Present ensures the Role exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementRBAC.Read.All |
| Update | Group.Read.All, DeviceManagementRBAC.ReadWrite.All |

## roleDefinition resource type

### Description

This resource configures an Intune Role Definition.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The unique idenfier for an entity. Read-only. | - |
| Description | Write | String | Description of the Role definition. | - |
| DisplayName | Key | String | Display Name of the Role definition. | - |
| IsBuiltIn | Write | Boolean | Type of Role. Set to True if it's built-in, or set to False if it's a custom role definition. | - |
| allowedResourceActions | Write | StringArray\[\] | List of allowed resource actions | - |
| notAllowedResourceActions | Write | StringArray\[\] | List of not allowed resource actions | - |
| roleScopeTagIds | Write | StringArray\[\] | Id of the Scope Tags to assign | - |
| Ensure | Write | String | Present ensures the Role exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | DeviceManagementRBAC.Read.All |
| Update | DeviceManagementRBAC.ReadWrite.All |

## settingCatalogAsrRulesPolicyWindows10 resource type

### Description

This resource configures a Intune Endpoint Protection Attack Surface Reduction rules policy for a Windows 10 Device. This resource returns ASR rules created using settings catalog settings.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Write | String | Identity of the endpoint protection attack surface protection rules policy for Windows 10. | - |
| DisplayName | Key | String | Display name of the endpoint protection attack surface protection rules policy for Windows 10. | - |
| Description | Write | String | Description of the endpoint protection attack surface protection rules policy for Windows 10. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Assignments of the endpoint protection. | - |
| AttackSurfaceReductionOnlyExclusions | Write | StringArray\[\] | Exclude files and paths from attack surface reduction rules | - |
| BlockAbuseOfExploitedVulnerableSignedDrivers | Write | String | This rule prevents an application from writing a vulnerable signed driver to disk. | `off`, `block`, `audit`, `warn` |
| BlockAbuseOfExploitedVulnerableSignedDrivers\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockAdobeReaderFromCreatingChildProcesses | Write | String | This rule prevents attacks by blocking Adobe Reader from creating processes. | `off`, `block`, `audit`, `warn` |
| BlockAdobeReaderFromCreatingChildProcesses\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockAllOfficeApplicationsFromCreatingChildProcesses | Write | String | This rule blocks Office apps from creating child processes. Office apps include Word, Excel, PowerPoint, OneNote, and Access. | `off`, `block`, `audit`, `warn` |
| BlockAllOfficeApplicationsFromCreatingChildProcesses\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions \(off: Off, block: Block, audit: Audit, warn: Warn\) | - |
| BlockCredentialStealingFromWindowsLocalSecurityAuthoritySubsystem | Write | String | This rule helps prevent credential stealing by locking down Local Security Authority Subsystem Service \(LSASS\). | `off`, `block`, `audit`, `warn` |
| BlockCredentialStealingFromWindowsLocalSecurityAuthoritySubsystem\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockExecutableContentFromEmailClientAndWebmail | Write | String | This rule blocks the following file types from launching from email opened within the Microsoft Outlook application, or Outlook.com and other popular webmail providers. | `off`, `block`, `audit`, `warn` |
| BlockExecutableContentFromEmailClientAndWebmail\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockExecutableFilesRunningUnlessTheyMeetPrevalenceAgeTrustedListCriterion | Write | String | This rule blocks executable files that don't meet a prevalence, age, or trusted list criteria, such as .exe, .dll, or .scr, from launching. | `off`, `block`, `audit`, `warn` |
| BlockExecutableFilesRunningUnlessTheyMeetPrevalenceAgeTrustedListCriterion\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockExecutionOfPotentiallyObfuscatedScripts | Write | String | This rule detects suspicious properties within an obfuscated script. | `off`, `block`, `audit`, `warn` |
| BlockExecutionOfPotentiallyObfuscatedScripts\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockJavaScriptOrVBScriptFromLaunchingDownloadedExecutableContent | Write | String | This rule prevents scripts from launching potentially malicious downloaded content. | `off`, `block`, `audit`, `warn` |
| BlockJavaScriptOrVBScriptFromLaunchingDownloadedExecutableContent\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockOfficeApplicationsFromCreatingExecutableContent | Write | String | This rule prevents Office apps, including Word, Excel, and PowerPoint, from creating potentially malicious executable content, by blocking malicious code from being written to disk. | `off`, `block`, `audit`, `warn` |
| BlockOfficeApplicationsFromCreatingExecutableContent\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockOfficeApplicationsFromInjectingCodeIntoOtherProcesses | Write | String | This rule blocks code injection attempts from Office apps into other processes. | `off`, `block`, `audit`, `warn` |
| BlockOfficeApplicationsFromInjectingCodeIntoOtherProcesses\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockOfficeCommunicationAppFromCreatingChildProcesses | Write | String | This rule prevents Outlook from creating child processes, while still allowing legitimate Outlook functions. | `off`, `block`, `audit`, `warn` |
| BlockOfficeCommunicationAppFromCreatingChildProcesses\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockPersistenceThroughWMIEventSubscription | Write | String | This rule prevents malware from abusing WMI to attain persistence on a device. | `off`, `block`, `audit`, `warn` |
| BlockProcessCreationsFromPSExecAndWMICommands | Write | String | This rule blocks processes created through PsExec and WMI from running. | `off`, `block`, `audit`, `warn` |
| BlockProcessCreationsFromPSExecAndWMICommands\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockRebootingMachineInSafeMode | Write | String | This rule prevents the execution of commands to restart machines in Safe Mode. | `off`, `block`, `audit`, `warn` |
| BlockRebootingMachineInSafeMode\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockUntrustedUnsignedProcessesThatRunFromUSB | Write | String | With this rule, admins can prevent unsigned or untrusted executable files from running from USB removable drives, including SD cards. | `off`, `block`, `audit`, `warn` |
| BlockUntrustedUnsignedProcessesThatRunFromUSB\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockUseOfCopiedOrImpersonatedSystemTools | Write | String | This rule blocks the use of executable files that are identified as copies of Windows system tools. These files are either duplicates or impostors of the original system tools. | `off`, `block`, `audit`, `warn` |
| BlockUseOfCopiedOrImpersonatedSystemTools\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockWebShellCreationForServers | Write | String | This rule blocks webshell creation for servers. | `off`, `block`, `audit`, `warn` |
| BlockWebshellCreationForServers\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| BlockWin32APICallsFromOfficeMacros | Write | String | This rule prevents VBA macros from calling Win32 APIs. | `off`, `block`, `audit`, `warn` |
| BlockWin32APICallsFromOfficeMacros\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| UseAdvancedProtectionAgainstRansomware | Write | String | This rule provides an extra layer of protection against ransomware. | `off`, `block`, `audit`, `warn` |
| UseAdvancedProtectionAgainstRansomware\_ASROnlyPerRuleExclusions | Write | StringArray\[\] | ASR Only Per Rule Exclusions | - |
| ControlledFolderAccessProtectedFolders | Write | StringArray\[\] | List of additional folders that need to be protected | - |
| ControlledFolderAccessAllowedApplications | Write | StringArray\[\] | List of apps that have access to protected folders. | - |
| EnableControlledFolderAccess | Write | String | This rule enables Controlled folder access which protects your data by checking apps against a list of known, trusted apps.values 0:disable, 1:enable, 2:audit | `0`, `1`, `2` |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## settingCatalogCustomPolicyWindows10 resource type

### Description

Intune Setting Catalog Custom Policy for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Description | Write | String | Policy description | - |
| Name | Key | String | Policy name | - |
| Platforms | Write | String | Platforms for this policy. Possible values are: none, android, iOS, macOS, windows10X, windows10, linux, unknownFutureValue. | `none`, `android`, `iOS`, `macOS`, `windows10X`, `windows10`, `linux`, `unknownFutureValue` |
| Technologies | Write | String | Technologies for this policy. Possible values are: none, mdm, windows10XManagement, configManager, appleRemoteManagement, microsoftSense, exchangeOnline, edgeMAM, linuxMdm, enrollment, endpointPrivilegeManagement, unknownFutureValue. | `none`, `mdm`, `windows10XManagement`, `configManager`, `appleRemoteManagement`, `microsoftSense`, `exchangeOnline`, `linuxMdm`, `enrollment`, `endpointPrivilegeManagement`, `unknownFutureValue` |
| TemplateReference | Write | MSFT\_MicrosoftGraphdeviceManagementConfigurationPolicyTemplateReference | Template reference information | - |
| Settings | Write | MSFT\_MicrosoftGraphdeviceManagementConfigurationSetting\[\] | Policy settings | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphDeviceManagementConfigurationPolicyTemplateReference

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| TemplateDisplayName | Write | String | Template Display Name of the referenced template. This property is read-only. | - |
| TemplateDisplayVersion | Write | String | Template Display Version of the referenced Template. This property is read-only. | - |
| TemplateFamily | Write | String | Template Family of the referenced Template. This property is read-only. Possible values are: none, endpointSecurityAntivirus, endpointSecurityDiskEncryption, endpointSecurityFirewall, endpointSecurityEndpointDetectionAndResponse, endpointSecurityAttackSurfaceReduction, endpointSecurityAccountProtection, endpointSecurityApplicationControl, endpointSecurityEndpointPrivilegeManagement, enrollmentConfiguration, appQuietTime, baseline, unknownFutureValue, deviceConfigurationScripts. | `none`, `endpointSecurityAntivirus`, `endpointSecurityDiskEncryption`, `endpointSecurityFirewall`, `endpointSecurityEndpointDetectionAndResponse`, `endpointSecurityAttackSurfaceReduction`, `endpointSecurityAccountProtection`, `endpointSecurityApplicationControl`, `endpointSecurityEndpointPrivilegeManagement`, `enrollmentConfiguration`, `appQuietTime`, `baseline`, `unknownFutureValue`, `deviceConfigurationScripts` |
| TemplateId | Write | String | Template id | - |

#### MSFT\_MicrosoftGraphDeviceManagementConfigurationSetting

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| SettingInstance | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationSettingInstance | Setting Instance | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |

#### MSFT\_MicrosoftGraphDeviceManagementConfigurationSettingInstance

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| SettingDefinitionId | Write | String | Setting Definition Id | - |
| SettingInstanceTemplateReference | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationSettingInstanceTemplateReference | Setting Instance Template Reference | - |
| ChoiceSettingCollectionValue | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationChoiceSettingValue\[\] | Choice setting collection value | - |
| ChoiceSettingValue | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationChoiceSettingValue | Choice setting value | - |
| GroupSettingCollectionValue | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationGroupSettingValue\[\] | A collection of GroupSetting values | - |
| GroupSettingValue | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationGroupSettingValue | GroupSetting value | - |
| SimpleSettingCollectionValue | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationSimpleSettingValue\[\] | Simple setting collection instance value | - |
| SimpleSettingValue | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationSimpleSettingValue | Simple setting instance value | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.deviceManagementConfigurationChoiceSettingCollectionInstance`, `#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance`, `#microsoft.graph.deviceManagementConfigurationGroupSettingCollectionInstance`, `#microsoft.graph.deviceManagementConfigurationGroupSettingInstance`, `#microsoft.graph.deviceManagementConfigurationSettingGroupCollectionInstance`, `#microsoft.graph.deviceManagementConfigurationSettingGroupInstance`, `#microsoft.graph.deviceManagementConfigurationSimpleSettingCollectionInstance`, `#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance` |

#### MSFT\_MicrosoftGraphDeviceManagementConfigurationSettingInstanceTemplateReference

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| SettingInstanceTemplateId | Write | String | Setting instance template id | - |

#### MSFT\_MicrosoftGraphDeviceManagementConfigurationChoiceSettingValue

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Children | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationSettingInstance\[\] | Child settings. | - |
| Value | Write | String | Choice setting value: an OptionDefinition ItemId. | - |
| SettingValueTemplateReference | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationSettingValueTemplateReference | Setting value template reference | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.deviceManagementConfigurationChoiceSettingValue`, `#microsoft.graph.deviceManagementConfigurationGroupSettingValue`, `#microsoft.graph.deviceManagementConfigurationSimpleSettingValue` |

#### MSFT\_MicrosoftGraphDeviceManagementConfigurationSettingValueTemplateReference

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| settingValueTemplateId | Write | String | Setting value template id | - |
| useTemplateDefault | Write | Boolean | Indicates whether to update policy setting value to match template setting default value | - |

#### MSFT\_MicrosoftGraphDeviceManagementConfigurationGroupSettingValue

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Children | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationSettingInstance\[\] | Collection of child setting instances contained within this GroupSetting | - |
| SettingValueTemplateReference | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationSettingValueTemplateReference | Setting value template reference | - |
| Value | Write | String | Choice setting value: an OptionDefinition ItemId. | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.deviceManagementConfigurationChoiceSettingValue`, `#microsoft.graph.deviceManagementConfigurationGroupSettingValue`, `#microsoft.graph.deviceManagementConfigurationSimpleSettingValue` |

#### MSFT\_MicrosoftGraphDeviceManagementConfigurationSimpleSettingValue

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IntValue | Write | UInt32 | Value of the integer setting. | - |
| StringValue | Write | String | Value of the string setting. | - |
| ValueState | Write | String | Gets or sets a value indicating the encryption state of the Value property. Possible values are: invalid, notEncrypted, encryptedValueToken. | `invalid`, `notEncrypted`, `encryptedValueToken` |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.deviceManagementConfigurationIntegerSettingValue`, `#microsoft.graph.deviceManagementConfigurationStringSettingValue`, `#microsoft.graph.deviceManagementConfigurationSecretSettingValue` |
| SettingValueTemplateReference | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationSettingValueTemplateReference | Setting value template reference | - |
| Children | Write | MSFT\_MicrosoftGraphDeviceManagementConfigurationSettingInstance\[\] | Child settings. | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## wifiConfigurationPolicyAndroidDeviceAdministrator resource type

### Description

This resource configures an Intune Wifi Configuration Policy Android Device Administrator Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune Policy. | - |
| DisplayName | Key | String | Display name of the Intune Policy. | - |
| Description | Write | String | Description of the Intune Policy. | - |
| ConnectAutomatically | Write | Boolean | Connect automatically. | - |
| ConnectWhenNetworkNameIsHidden | Write | Boolean | Connect when network name is hidden. | - |
| NetworkName | Write | String | Network name. | - |
| Ssid | Write | String | SSID. | - |
| WiFiSecurityType | Write | String | Wi-Fi security type. | `open`, `wpaEnterprise`, `wpa2Enterprise` |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | DeviceManagementConfiguration.Read.All |
| Update | DeviceManagementConfiguration.ReadWrite.All |

## wifiConfigurationPolicyAndroidEnterpriseDeviceOwner resource type

### Description

This resource configures an Intune Wifi Configuration Policy Android Enterprise Device Owner Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune policy | - |
| DisplayName | Key | String | Disaply name of the Intune policy | - |
| Description | Write | String | Description of the Intune policy | - |
| ConnectAutomatically | Write | Boolean | If the network is in range, automatically connect. | - |
| ConnectWhenNetworkNameIsHidden | Write | Boolean | Don't show this Wi-Fi network on an end-user's device in the list of available networks. The SSID will not be broadcasted. | - |
| NetworkName | Write | String | Network name. | - |
| PreSharedKey | Write | String | Pre shared key. | - |
| PreSharedKeyIsSet | Write | Boolean | Pre shared key is set. | - |
| ProxyAutomaticConfigurationUrl | Write | String | URL of the automatic proxy. | - |
| ProxyExclusionList | Write | String | Exclusion list of the proxy. | - |
| ProxyManualAddress | Write | String | Address of the proxy. | - |
| ProxyManualPort | Write | UInt32 | Port of the proxy. | - |
| ProxySettings | Write | String | Proxy setting type. | `none`, `manual`, `automatic` |
| Ssid | Write | String | Service Set Identifier. The name of the Wi-Fi connection. | - |
| WiFiSecurityType | Write | String | Type of Wi-Fi profile. | `open`, `wep`, `wpaPersonal`, `wpaEnterprise` |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## wifiConfigurationPolicyAndroidEnterpriseWorkProfile resource type

### Description

This resource configures an Intune Wifi Configuration Policy Android Enterprise Work Profile Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune policy. | - |
| DisplayName | Key | String | Display name of the Intune policy. | - |
| Description | Write | String | Description of the Intune policy. | - |
| ConnectAutomatically | Write | Boolean | Connect automatically. | - |
| ConnectWhenNetworkNameIsHidden | Write | Boolean | Connect when network name is hidden. | - |
| NetworkName | Write | String | Network name. | - |
| Ssid | Write | String | SSID. | - |
| WiFiSecurityType | Write | String | Wi-Fi security. | `open`, `wpaEnterprise`, `wpa2Enterprise` |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## wifiConfigurationPolicyAndroidForWork resource type

### Description

This resource configures an Intune Wifi Configuration Policy Android For Work Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune policy. | - |
| DisplayName | Key | String | Display name of the Intune policy. | - |
| Description | Write | String | Description of the Intune policy. | - |
| ConnectAutomatically | Write | Boolean | Connect automatically | - |
| ConnectWhenNetworkNameIsHidden | Write | Boolean | Connect when network name is hidden | - |
| NetworkName | Write | String | Network name | - |
| Ssid | Write | String | SSID | - |
| WiFiSecurityType | Write | String | Wi-Fi security | `open`, `wpaEnterprise`, `wpa2Enterprise` |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## wifiConfigurationPolicyAndroidOpenSourceProject resource type

### Description

This resource configures an Intune Wifi Configuration Policy Android Open Source Project Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune policy. | - |
| DisplayName | Key | String | Display name of the Intune policy. | - |
| Description | Write | String | Description of the Intune policy. | - |
| ConnectAutomatically | Write | Boolean | Connect automatically to the network. | - |
| ConnectWhenNetworkNameIsHidden | Write | Boolean | Define if the network should be connected if hidden. | - |
| NetworkName | Write | String | Define the network name. | - |
| PreSharedKey | Write | String | Define the pre-shared key. | - |
| PreSharedKeyIsSet | Write | Boolean | Define if the pre-shared key is set. | - |
| Ssid | Write | String | Define the SSID. | - |
| WiFiSecurityType | Write | String | Define the Wifi security type. | `open`, `wep`, `wpaPersonal`, `wpaEnterprise` |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## wifiConfigurationPolicyiOS resource type

### Description

This resource configures an Intune Wifi Configuration Policy for iOS Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune policy. | - |
| DisplayName | Key | String | Display name of the Intune policy. | - |
| Description | Write | String | Description of the Intune policy. | - |
| ConnectAutomatically | Write | Boolean | Connect automatically | - |
| ConnectWhenNetworkNameIsHidden | Write | Boolean | Connect when network name is hidden | - |
| DisableMacAddressRandomization | Write | Boolean | Disable the MAC address randomization. | - |
| NetworkName | Write | String | Network name | - |
| PreSharedKey | Write | String | Pre shared key | - |
| ProxyAutomaticConfigurationUrl | Write | String | Proxy automatic configuration url | - |
| ProxyManualAddress | Write | String | Proxy manual address | - |
| ProxyManualPort | Write | UInt32 | Proxy manual port | - |
| ProxySettings | Write | String | Proxy settings | `none`, `manual`, `automatic` |
| Ssid | Write | String | SSID | - |
| WiFiSecurityType | Write | String | Wi-Fi security | `open`, `wpaPersonal`, `wpaEnterprise`, `wep`, `wpa2Personal`, `wpa2Enterprise` |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## wifiConfigurationPolicymacOS resource type

### Description

This resource configures an Intune Wifi Configuration Policy for MacOS Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune policy. | - |
| DisplayName | Key | String | Display name of the Intune policy. | - |
| Description | Write | String | Description of the Intune policy. | - |
| ConnectAutomatically | Write | Boolean | Connect automatically | - |
| ConnectWhenNetworkNameIsHidden | Write | Boolean | Connect when network name is hidden | - |
| NetworkName | Write | String | Network name | - |
| PreSharedKey | Write | String | Pre shared key | - |
| ProxyAutomaticConfigurationUrl | Write | String | Proxy automatic configuration url | - |
| ProxyManualAddress | Write | String | Proxy manual address | - |
| ProxyManualPort | Write | UInt32 | Proxy manual port | - |
| ProxySettings | Write | String | Proxy settings | `none`, `manual`, `automatic` |
| Ssid | Write | String | SSID | - |
| WiFiSecurityType | Write | String | Wi-Fi security | `open`, `wpaPersonal`, `wpaEnterprise`, `wep`, `wpa2Personal`, `wpa2Enterprise` |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## wifiConfigurationPolicyWindows10 resource type

### Description

This resource configures an Intune Wifi Configuration Policy for Windows10 Device.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | Id of the Intune policy. | - |
| DisplayName | Key | String | Display name of the Intune policy. | - |
| Description | Write | String | Description of the Intune policy. | - |
| ConnectAutomatically | Write | Boolean | Connect automatically | - |
| ConnectToPreferredNetwork | Write | Boolean | Connect to preferred network | - |
| ConnectWhenNetworkNameIsHidden | Write | Boolean | Connect when network name is hidden | - |
| ForceFIPSCompliance | Write | Boolean | Force FIPS compliance | - |
| MeteredConnectionLimit | Write | String | Metered connection limit | `unrestricted`, `fixed`, `variable` |
| NetworkName | Write | String | Network name | - |
| PreSharedKey | Write | String | Pre shared key | - |
| ProxyAutomaticConfigurationUrl | Write | String | Proxy automatic configuration url | - |
| ProxyManualAddress | Write | String | Proxy manual address | - |
| ProxyManualPort | Write | UInt32 | Proxy manual port | - |
| ProxySetting | Write | String | Proxy setting | `none`, `manual`, `automatic` |
| Ssid | Write | String | SSID | - |
| WifiSecurityType | Write | String | Wi-Fi security | `open`, `wpaPersonal`, `wpaEnterprise`, `wep`, `wpa2Personal`, `wpa2Enterprise` |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## windowsAutopilotDeploymentProfileAzureADHybridJoined resource type

### Description

Intune Windows Autopilot Deployment Profile Microsoft Entra Hybrid Joined

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| HybridAzureADJoinSkipConnectivityCheck | Write | Boolean | The Autopilot Hybrid Microsoft Entra join flow will continue even if it does not establish domain controller connectivity during OOBE. | - |
| Description | Write | String | Description of the profile | - |
| DeviceNameTemplate | Write | String | The template used to name the AutoPilot Device. This can be a custom text and can also contain either the serial number of the device, or a randomly generated number. The total length of the text generated by the template can be no more than 15 characters. | - |
| DeviceType | Write | String | The AutoPilot device type that this profile is applicable to. Possible values are: windowsPc, surfaceHub2. | `windowsPc`, `surfaceHub2`, `holoLens`, `surfaceHub2S`, `virtualMachine`, `unknownFutureValue` |
| DisplayName | Key | String | Name of the profile | - |
| EnableWhiteGlove | Write | Boolean | Enable Autopilot White Glove for the profile. | - |
| EnrollmentStatusScreenSettings | Write | MSFT\_MicrosoftGraphwindowsEnrollmentStatusScreenSettings | Enrollment status screen setting | - |
| ExtractHardwareHash | Write | Boolean | HardwareHash Extraction for the profile | - |
| Language | Write | String | Language configured on the device | - |
| ManagementServiceAppId | Write | String | AzureAD management app ID used during client device-based enrollment discovery | - |
| OutOfBoxExperienceSettings | Write | MSFT\_MicrosoftGraphoutOfBoxExperienceSettings | Out of box experience setting | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphWindowsEnrollmentStatusScreenSettings

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AllowDeviceUseBeforeProfileAndAppInstallComplete | Write | Boolean | Allow or block user to use device before profile and app installation complete | - |
| AllowDeviceUseOnInstallFailure | Write | Boolean | Allow the user to continue using the device on installation failure | - |
| AllowLogCollectionOnInstallFailure | Write | Boolean | Allow or block log collection on installation failure | - |
| BlockDeviceSetupRetryByUser | Write | Boolean | Allow the user to retry the setup on installation failure | - |
| CustomErrorMessage | Write | String | Set custom error message to show upon installation failure | - |
| HideInstallationProgress | Write | Boolean | Show or hide installation progress to user | - |
| InstallProgressTimeoutInMinutes | Write | UInt32 | Set installation progress timeout in minutes | - |

#### MSFT\_MicrosoftGraphOutOfBoxExperienceSettings

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DeviceUsageType | Write | String | AAD join authentication type. Possible values are: singleUser, shared. | `singleUser`, `shared` |
| HideEscapeLink | Write | Boolean | If set to true, then the user can't start over with different account, on company sign-in | - |
| HideEULA | Write | Boolean | Show or hide EULA to user | - |
| HidePrivacySettings | Write | Boolean | Show or hide privacy settings to user | - |
| SkipKeyboardSelectionPage | Write | Boolean | If set, then skip the keyboard selection page if Language and Region are set | - |
| UserType | Write | String | Type of user. Possible values are: administrator, standard. | `administrator`, `standard` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementServiceConfig.Read.All |
| Update | Group.Read.All, DeviceManagementServiceConfig.ReadWrite.All |

## windowsAutopilotDeploymentProfileAzureADJoined resource type

### Description

Intune Windows Autopilot Deployment Profile Microsoft Entra Joined

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Description | Write | String | Description of the profile | - |
| DeviceNameTemplate | Write | String | The template used to name the AutoPilot Device. This can be a custom text and can also contain either the serial number of the device, or a randomly generated number. The total length of the text generated by the template can be no more than 15 characters. | - |
| DeviceType | Write | String | The AutoPilot device type that this profile is applicable to. Possible values are: windowsPc, surfaceHub2. | `windowsPc`, `surfaceHub2`, `holoLens`, `surfaceHub2S`, `virtualMachine`, `unknownFutureValue` |
| DisplayName | Key | String | Name of the profile | - |
| EnableWhiteGlove | Write | Boolean | Enable Autopilot White Glove for the profile. | - |
| EnrollmentStatusScreenSettings | Write | MSFT\_MicrosoftGraphwindowsEnrollmentStatusScreenSettings1 | Enrollment status screen setting | - |
| ExtractHardwareHash | Write | Boolean | HardwareHash Extraction for the profile | - |
| Language | Write | String | Language configured on the device | - |
| ManagementServiceAppId | Write | String | AzureAD management app ID used during client device-based enrollment discovery | - |
| OutOfBoxExperienceSettings | Write | MSFT\_MicrosoftGraphoutOfBoxExperienceSettings1 | Out of box experience setting | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphWindowsEnrollmentStatusScreenSettings1

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AllowDeviceUseBeforeProfileAndAppInstallComplete | Write | Boolean | Allow or block user to use device before profile and app installation complete | - |
| AllowDeviceUseOnInstallFailure | Write | Boolean | Allow the user to continue using the device on installation failure | - |
| AllowLogCollectionOnInstallFailure | Write | Boolean | Allow or block log collection on installation failure | - |
| BlockDeviceSetupRetryByUser | Write | Boolean | Allow the user to retry the setup on installation failure | - |
| CustomErrorMessage | Write | String | Set custom error message to show upon installation failure | - |
| HideInstallationProgress | Write | Boolean | Show or hide installation progress to user | - |
| InstallProgressTimeoutInMinutes | Write | UInt32 | Set installation progress timeout in minutes | - |

#### MSFT\_MicrosoftGraphOutOfBoxExperienceSettings1

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DeviceUsageType | Write | String | AAD join authentication type. Possible values are: singleUser, shared. | `singleUser`, `shared` |
| HideEscapeLink | Write | Boolean | If set to true, then the user can't start over with different account, on company sign-in | - |
| HideEULA | Write | Boolean | Show or hide EULA to user | - |
| HidePrivacySettings | Write | Boolean | Show or hide privacy settings to user | - |
| SkipKeyboardSelectionPage | Write | Boolean | If set, then skip the keyboard selection page if Language and Region are set | - |
| UserType | Write | String | Type of user. Possible values are: administrator, standard. | `administrator`, `standard` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementServiceConfig.Read.All |
| Update | Group.Read.All, DeviceManagementServiceConfig.ReadWrite.All |

## windowsInformationProtectionPolicyWindows10MdmEnrolled resource type

### Description

Intune Windows Information Protection Policy for Windows10 Mdm Enrolled

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| DisplayName | Key | String | Policy display name. | - |
| AzureRightsManagementServicesAllowed | Write | Boolean | Specifies whether to allow Azure RMS encryption for WIP | - |
| DataRecoveryCertificate | Write | MSFT\_MicrosoftGraphwindowsInformationProtectionDataRecoveryCertificate | Specifies a recovery certificate that can be used for data recovery of encrypted files. This is the same as the data recovery agent\(DRA\) certificate for encrypting file system\(EFS\) | - |
| EnforcementLevel | Write | String | WIP enforcement level.See the Enum definition for supported values. Possible values are: noProtection, encryptAndAuditOnly, encryptAuditAndPrompt, encryptAuditAndBlock. | `noProtection`, `encryptAndAuditOnly`, `encryptAuditAndPrompt`, `encryptAuditAndBlock` |
| EnterpriseDomain | Write | String | Primary enterprise domain | - |
| EnterpriseInternalProxyServers | Write | MSFT\_MicrosoftGraphwindowsInformationProtectionResourceCollection\[\] | This is the comma-separated list of internal proxy servers. For example, '157.54.14.28, 157.54.11.118, 10.202.14.167, 157.53.14.163, 157.69.210.59'. These proxies have been configured by the admin to connect to specific resources on the Internet. They are considered to be enterprise network locations. The proxies are only leveraged in configuring the EnterpriseProxiedDomains policy to force traffic to the matched domains through these proxies | - |
| EnterpriseIPRanges | Write | MSFT\_MicrosoftGraphwindowsInformationProtectionIPRangeCollection\[\] | Sets the enterprise IP ranges that define the computers in the enterprise network. Data that comes from those computers will be considered part of the enterprise and protected. These locations will be considered a safe destination for enterprise data to be shared to | - |
| EnterpriseIPRangesAreAuthoritative | Write | Boolean | Boolean value that tells the client to accept the configured list and not to use heuristics to attempt to find other subnets. Default is false | - |
| EnterpriseNetworkDomainNames | Write | MSFT\_MicrosoftGraphwindowsInformationProtectionResourceCollection\[\] | This is the list of domains that comprise the boundaries of the enterprise. Data from one of these domains that is sent to a device will be considered enterprise data and protected These locations will be considered a safe destination for enterprise data to be shared to | - |
| EnterpriseProtectedDomainNames | Write | MSFT\_MicrosoftGraphwindowsInformationProtectionResourceCollection\[\] | List of enterprise domains to be protected | - |
| EnterpriseProxiedDomains | Write | MSFT\_MicrosoftGraphwindowsInformationProtectionProxiedDomainCollection\[\] | Contains a list of Enterprise resource domains hosted in the cloud that need to be protected. Connections to these resources are considered enterprise data. If a proxy is paired with a cloud resource, traffic to the cloud resource will be routed through the enterprise network via the denoted proxy server \(on Port 80\). A proxy server used for this purpose must also be configured using the EnterpriseInternalProxyServers policy | - |
| EnterpriseProxyServers | Write | MSFT\_MicrosoftGraphwindowsInformationProtectionResourceCollection\[\] | This is a list of proxy servers. Any server not on this list is considered non-enterprise | - |
| EnterpriseProxyServersAreAuthoritative | Write | Boolean | Boolean value that tells the client to accept the configured list of proxies and not try to detect other work proxies. Default is false | - |
| ExemptApps | Write | MSFT\_MicrosoftGraphwindowsInformationProtectionApp\[\] | Exempt applications can also access enterprise data, but the data handled by those applications are not protected. This is because some critical enterprise applications may have compatibility problems with encrypted data. | - |
| IconsVisible | Write | Boolean | Determines whether overlays are added to icons for WIP protected files in Explorer and enterprise only app tiles in the Start menu. Starting in Windows 10, version 1703 this setting also configures the visibility of the WIP icon in the title bar of a WIP-protected app | - |
| IndexingEncryptedStoresOrItemsBlocked | Write | Boolean | This switch is for the Windows Search Indexer, to allow or disallow indexing of items | - |
| NeutralDomainResources | Write | MSFT\_MicrosoftGraphwindowsInformationProtectionResourceCollection\[\] | List of domain names that can used for work or personal resource | - |
| ProtectedApps | Write | MSFT\_MicrosoftGraphwindowsInformationProtectionApp\[\] | Protected applications can access enterprise data and the data handled by those applications are protected with encryption | - |
| ProtectionUnderLockConfigRequired | Write | Boolean | Specifies whether the protection under lock feature \(also known as encrypt under pin\) should be configured | - |
| RevokeOnUnenrollDisabled | Write | Boolean | This policy controls whether to revoke the WIP keys when a device unenrolls from the management service. If set to 1 \(Don't revoke keys\), the keys will not be revoked and the user will continue to have access to protected files after unenrollment. If the keys are not revoked, there will be no revoked file cleanup subsequently. | - |
| RightsManagementServicesTemplateId | Write | String | TemplateID GUID to use for RMS encryption. The RMS template allows the IT admin to configure the details about who has access to RMS-protected file and how long they have access | - |
| SmbAutoEncryptedFileExtensions | Write | MSFT\_MicrosoftGraphwindowsInformationProtectionResourceCollection\[\] | Specifies a list of file extensions, so that files with these extensions are encrypted when copying from an SMB share within the corporate boundary | - |
| Description | Write | String | The policy's description. | - |
| Assignments | Write | WindowsInformationProtectionPolicyWindows10MdmEnrolledPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### WindowsInformationProtectionPolicyWindows10MdmEnrolledPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphWindowsInformationProtectionDataRecoveryCertificate

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Certificate | Write | String | Data recovery Certificate | - |
| Description | Write | String | Data recovery Certificate description | - |
| ExpirationDateTime | Write | String | Data recovery Certificate expiration datetime | - |
| SubjectName | Write | String | Data recovery Certificate subject name | - |

#### MSFT\_MicrosoftGraphWindowsInformationProtectionResourceCollection

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Write | String | Display name | - |
| Resources | Write | StringArray\[\] | Collection of resources | - |

#### MSFT\_MicrosoftGraphWindowsInformationProtectionIPRangeCollection

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Write | String | Display name | - |
| Ranges | Write | MSFT\_MicrosoftGraphIpRange\[\] | Collection of ip ranges | - |

#### MSFT\_MicrosoftGraphIpRange

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| CidrAddress | Write | String | IPv4 address in CIDR notation. Not nullable. | - |
| LowerAddress | Write | String | Lower address. | - |
| UpperAddress | Write | String | Upper address. | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.iPv4CidrRange`, `#microsoft.graph.iPv6CidrRange`, `#microsoft.graph.iPv4Range`, `#microsoft.graph.iPv6Range` |

#### MSFT\_MicrosoftGraphWindowsInformationProtectionProxiedDomainCollection

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Write | String | Display name | - |
| ProxiedDomains | Write | MSFT\_MicrosoftGraphProxiedDomain\[\] | Collection of proxied domains | - |

#### MSFT\_MicrosoftGraphProxiedDomain

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IpAddressOrFQDN | Write | String | The IP address or FQDN | - |
| Proxy | Write | String | Proxy IP or FQDN | - |

#### MSFT\_MicrosoftGraphWindowsInformationProtectionApp

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Denied | Write | Boolean | If true, app is denied protection or exemption. | - |
| Description | Write | String | The app's description. | - |
| DisplayName | Write | String | App display name. | - |
| ProductName | Write | String | The product name. | - |
| PublisherName | Write | String | The publisher name | - |
| BinaryName | Write | String | The binary name. | - |
| BinaryVersionHigh | Write | String | The high binary version. | - |
| BinaryVersionLow | Write | String | The lower binary version. | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.windowsInformationProtectionDesktopApp`, `#microsoft.graph.windowsInformationProtectionStoreApp` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementApps.Read.All |
| Update | Group.Read.All, DeviceManagementApps.ReadWrite.All |

## windowsUpdateForBusinessFeatureUpdateProfileWindows10 resource type

### Description

Intune Windows Update For Business Feature Update Profile for Windows10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| DisplayName | Key | String | The display name of the profile. | - |
| Description | Write | String | The description of the profile which is specified by the user. | - |
| FeatureUpdateVersion | Write | String | The feature update version that will be deployed to the devices targeted by this profile. The version could be any supported version for example 1709, 1803 or 1809 and so on. | - |
| InstallFeatureUpdatesOptional | Write | Boolean | If true, the Windows 11 update will become optional | - |
| InstallLatestWindows10OnWindows11IneligibleDevice | Write | Boolean | If true, the latest Microsoft Windows 10 update will be installed on devices ineligible for Microsoft Windows 11. Cannot be changed after creation of the policy. | - |
| RolloutSettings | Write | MSFT\_MicrosoftGraphwindowsUpdateRolloutSettings | The windows update rollout settings, including offer start date time, offer end date time, and days between each set of offers. For 'as soon as possible' installation, set this setting to $null or do not configure it. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphWindowsUpdateRolloutSettings

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| OfferEndDateTimeInUTC | Write | String | The feature update's ending of release date and time to be set, update, and displayed for a feature Update profile for example: 2020-06-09T10:00:00Z. | - |
| OfferIntervalInDays | Write | UInt32 | The number of day\(s\) between each set of offers to be set, updated, and displayed for a feature update profile, for example: if OfferStartDateTimeInUTC is 2020-06-09T10:00:00Z, and OfferIntervalInDays is 1, then the next two sets of offers will be made consecutively on 2020-06-10T10:00:00Z \(next day at the same specified time\) and 2020-06-11T10:00:00Z \(next next day at the same specified time\) with 1 day in between each set of offers. | - |
| OfferStartDateTimeInUTC | Write | String | The feature update's starting date and time to be set, update, and displayed for a feature Update profile for example: 2020-06-09T10:00:00Z. | - |

### RolloutSettings

The RolloutSettings for this resource have the following constraints and notes:

- When creating a policy:

  - If only a start date is specified, then the start date must be at least today.

    - If the desired state date is before the current date, it will be adjusted to the current date.

  - If a start and end date is specified, the start date must be the current date + 2 days, and  
    the end date must be at least one day after the start date.

    - If the start date is before the current date + 2 days, it will be adjusted to this date.

- When updating a policy:

  - If only a start date is specified, then the start date must either be the date from the current  
    configuration or the current date \(or later\).

    - If the desired state date is before the current date, it will be adjusted to the current date.

  - If a start and end date is specified, the start date must be the current date + 2 days, and  
    the end date must be at least one day after the start date.

    - If the start date is before the current date + 2 days, it will be adjusted to this date.

- When testing a policy:

  - If the policy is missing and the start and end date are before the current date, it will return true.
  - If the start date is different but before the current start date or time, it will return true.

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## windowsUpdateForBusinessRingUpdateProfileWindows10 resource type

### Description

Intune Windows Update For Business Ring Update Profile for Windows 10

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| DisplayName | Key | String | Admin provided name of the device configuration. | - |
| AllowWindows11Upgrade | Write | Boolean | When TRUE, allows eligible Windows 10 devices to upgrade to Windows 11. When FALSE, implies the device stays on the existing operating system. Returned by default. Query parameters are not supported. | - |
| AutomaticUpdateMode | Write | String | The Automatic Update Mode. Possible values are: UserDefined, NotifyDownload, AutoInstallAtMaintenanceTime, AutoInstallAndRebootAtMaintenanceTime, AutoInstallAndRebootAtScheduledTime, AutoInstallAndRebootWithoutEndUserControl, WindowsDefault. UserDefined is the default value, no intent. Returned by default. Query parameters are not supported. Possible values are: userDefined, notifyDownload, autoInstallAtMaintenanceTime, autoInstallAndRebootAtMaintenanceTime, autoInstallAndRebootAtScheduledTime, autoInstallAndRebootWithoutEndUserControl, windowsDefault. | `userDefined`, `notifyDownload`, `autoInstallAtMaintenanceTime`, `autoInstallAndRebootAtMaintenanceTime`, `autoInstallAndRebootAtScheduledTime`, `autoInstallAndRebootWithoutEndUserControl`, `windowsDefault` |
| AutoRestartNotificationDismissal | Write | String | Specify the method by which the auto-restart required notification is dismissed. Possible values are: NotConfigured, Automatic, User. Returned by default. Query parameters are not supported. Possible values are: notConfigured, automatic, user, unknownFutureValue. | `notConfigured`, `automatic`, `user`, `unknownFutureValue` |
| BusinessReadyUpdatesOnly | Write | String | Determines which branch devices will receive their updates from. Possible values are: UserDefined, All, BusinessReadyOnly, WindowsInsiderBuildFast, WindowsInsiderBuildSlow, WindowsInsiderBuildRelease. Returned by default. Query parameters are not supported. Possible values are: userDefined, all, businessReadyOnly, windowsInsiderBuildFast, windowsInsiderBuildSlow, windowsInsiderBuildRelease. | `userDefined`, `all`, `businessReadyOnly`, `windowsInsiderBuildFast`, `windowsInsiderBuildSlow`, `windowsInsiderBuildRelease` |
| DeadlineForFeatureUpdatesInDays | Write | UInt32 | Number of days before feature updates are installed automatically with valid range from 0 to 30 days. Returned by default. Query parameters are not supported. | - |
| DeadlineForQualityUpdatesInDays | Write | UInt32 | Number of days before quality updates are installed automatically with valid range from 0 to 30 days. Returned by default. Query parameters are not supported. | - |
| DeadlineGracePeriodInDays | Write | UInt32 | Number of days after deadline until restarts occur automatically with valid range from 0 to 7 days. Returned by default. Query parameters are not supported. | - |
| DeliveryOptimizationMode | Write | String | The Delivery Optimization Mode. Possible values are: UserDefined, HttpOnly, HttpWithPeeringNat, HttpWithPeeringPrivateGroup, HttpWithInternetPeering, SimpleDownload, BypassMode. UserDefined allows the user to set. Returned by default. Query parameters are not supported. Possible values are: userDefined, httpOnly, httpWithPeeringNat, httpWithPeeringPrivateGroup, httpWithInternetPeering, simpleDownload, bypassMode. | `userDefined`, `httpOnly`, `httpWithPeeringNat`, `httpWithPeeringPrivateGroup`, `httpWithInternetPeering`, `simpleDownload`, `bypassMode` |
| DriversExcluded | Write | Boolean | When TRUE, excludes Windows update Drivers. When FALSE, does not exclude Windows update Drivers. Returned by default. Query parameters are not supported. | - |
| EngagedRestartDeadlineInDays | Write | UInt32 | Deadline in days before automatically scheduling and executing a pending restart outside of active hours, with valid range from 2 to 30 days. Returned by default. Query parameters are not supported. | - |
| EngagedRestartSnoozeScheduleInDays | Write | UInt32 | Number of days a user can snooze Engaged Restart reminder notifications with valid range from 1 to 3 days. Returned by default. Query parameters are not supported. | - |
| EngagedRestartTransitionScheduleInDays | Write | UInt32 | Number of days before transitioning from Auto Restarts scheduled outside of active hours to Engaged Restart, which requires the user to schedule, with valid range from 0 to 30 days. Returned by default. Query parameters are not supported. | - |
| FeatureUpdatesDeferralPeriodInDays | Write | UInt32 | Defer Feature Updates by these many days with valid range from 0 to 30 days. Returned by default. Query parameters are not supported. | - |
| FeatureUpdatesPaused | Write | Boolean | When TRUE, assigned devices are paused from receiving feature updates for up to 35 days from the time you pause the ring. When FALSE, does not pause Feature Updates. Returned by default. Query parameters are not supported.s | - |
| FeatureUpdatesPauseExpiryDateTime | Write | String | The Feature Updates Pause Expiry datetime. This value is 35 days from the time admin paused or extended the pause for the ring. Returned by default. Query parameters are not supported. | - |
| FeatureUpdatesPauseStartDate | Write | String | The Feature Updates Pause start date. This value is the time when the admin paused or extended the pause for the ring. Returned by default. Query parameters are not supported. This property is read-only. | - |
| FeatureUpdatesRollbackStartDateTime | Write | String | The Feature Updates Rollback Start datetime.This value is the time when the admin rolled back the Feature update for the ring.Returned by default.Query parameters are not supported. | - |
| FeatureUpdatesRollbackWindowInDays | Write | UInt32 | The number of days after a Feature Update for which a rollback is valid with valid range from 2 to 60 days. Returned by default. Query parameters are not supported. | - |
| InstallationSchedule | Write | MSFT\_MicrosoftGraphwindowsUpdateInstallScheduleType | The Installation Schedule. Possible values are: ActiveHoursStart, ActiveHoursEnd, ScheduledInstallDay, ScheduledInstallTime. Returned by default. Query parameters are not supported. | - |
| MicrosoftUpdateServiceAllowed | Write | Boolean | When TRUE, allows Microsoft Update Service. When FALSE, does not allow Microsoft Update Service. Returned by default. Query parameters are not supported. | - |
| PostponeRebootUntilAfterDeadline | Write | Boolean | When TRUE the device should wait until deadline for rebooting outside of active hours. When FALSE the device should not wait until deadline for rebooting outside of active hours. Returned by default. Query parameters are not supported. | - |
| PrereleaseFeatures | Write | String | The Pre-Release Features. Possible values are: UserDefined, SettingsOnly, SettingsAndExperimentations, NotAllowed. UserDefined is the default value, no intent. Returned by default. Query parameters are not supported. Possible values are: userDefined, settingsOnly, settingsAndExperimentations, notAllowed. | `userDefined`, `settingsOnly`, `settingsAndExperimentations`, `notAllowed` |
| QualityUpdatesDeferralPeriodInDays | Write | UInt32 | Defer Quality Updates by these many days with valid range from 0 to 30 days. Returned by default. Query parameters are not supported. | - |
| QualityUpdatesPaused | Write | Boolean | When TRUE, assigned devices are paused from receiving quality updates for up to 35 days from the time you pause the ring. When FALSE, does not pause Quality Updates. Returned by default. Query parameters are not supported. | - |
| QualityUpdatesPauseExpiryDateTime | Write | String | The Quality Updates Pause Expiry datetime. This value is 35 days from the time admin paused or extended the pause for the ring. Returned by default. Query parameters are not supported. | - |
| QualityUpdatesPauseStartDate | Write | String | The Quality Updates Pause start date. This value is the time when the admin paused or extended the pause for the ring. Returned by default. Query parameters are not supported. This property is read-only. | - |
| QualityUpdatesRollbackStartDateTime | Write | String | The Quality Updates Rollback Start datetime. This value is the time when the admin rolled back the Quality update for the ring. Returned by default. Query parameters are not supported. | - |
| ScheduleImminentRestartWarningInMinutes | Write | UInt32 | Specify the period for auto-restart imminent warning notifications. Supported values: 15, 30 or 60 \(minutes\). Returned by default. Query parameters are not supported. | - |
| ScheduleRestartWarningInHours | Write | UInt32 | Specify the period for auto-restart warning reminder notifications. Supported values: 2, 4, 8, 12 or 24 \(hours\). Returned by default. Query parameters are not supported. | - |
| SkipChecksBeforeRestart | Write | Boolean | When TRUE, skips all checks before restart: Battery level = 40%, User presence, Display Needed, Presentation mode, Full screen mode, phone call state, game mode etc. When FALSE, does not skip all checks before restart. Returned by default. Query parameters are not supported. | - |
| UpdateNotificationLevel | Write | String | Specifies what Windows Update notifications users see. Possible values are: NotConfigured, DefaultNotifications, RestartWarningsOnly, DisableAllNotifications. Returned by default. Query parameters are not supported. Possible values are: notConfigured, defaultNotifications, restartWarningsOnly, disableAllNotifications, unknownFutureValue. | `notConfigured`, `defaultNotifications`, `restartWarningsOnly`, `disableAllNotifications`, `unknownFutureValue` |
| UpdateWeeks | Write | String | Schedule the update installation on the weeks of the month. Possible values are: UserDefined, FirstWeek, SecondWeek, ThirdWeek, FourthWeek, EveryWeek. Returned by default. Query parameters are not supported. Possible values are: userDefined, firstWeek, secondWeek, thirdWeek, fourthWeek, everyWeek, unknownFutureValue. | `userDefined`, `firstWeek`, `secondWeek`, `thirdWeek`, `fourthWeek`, `everyWeek`, `unknownFutureValue` |
| UserPauseAccess | Write | String | Specifies whether to enable end user's access to pause software updates. Possible values are: NotConfigured, Enabled, Disabled. Returned by default. Query parameters are not supported. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| UserWindowsUpdateScanAccess | Write | String | Specifies whether to disable user's access to scan Windows Update. Possible values are: NotConfigured, Enabled, Disabled. Returned by default. Query parameters are not supported. Possible values are: notConfigured, enabled, disabled. | `notConfigured`, `enabled`, `disabled` |
| Description | Write | String | Admin provided description of the Device Configuration. | - |
| Assignments | Write | MSFT\_DeviceManagementConfigurationPolicyAssignments\[\] | Represents the assignment to the Intune policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_DeviceManagementConfigurationPolicyAssignments

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dataType | Write | String | The type of the target assignment. | `#microsoft.graph.groupAssignmentTarget`, `#microsoft.graph.allLicensedUsersAssignmentTarget`, `#microsoft.graph.allDevicesAssignmentTarget`, `#microsoft.graph.exclusionGroupAssignmentTarget`, `#microsoft.graph.configurationManagerCollectionAssignmentTarget` |
| deviceAndAppManagementAssignmentFilterType | Write | String | The type of filter of the target assignment i.e. Exclude or Include. Possible values are:none, include, exclude. | `none`, `include`, `exclude` |
| deviceAndAppManagementAssignmentFilterId | Write | String | The Id of the filter for the target assignment. | - |
| groupId | Write | String | The group Id that is the target of the assignment. | - |
| groupDisplayName | Write | String | The group Display Name that is the target of the assignment. | - |
| collectionId | Write | String | The collection Id that is the target of the assignment.\(ConfigMgr\) | - |

#### MSFT\_MicrosoftGraphWindowsUpdateInstallScheduleType

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ActiveHoursEnd | Write | String | Active Hours End | - |
| ActiveHoursStart | Write | String | Active Hours Start | - |
| ScheduledInstallDay | Write | String | Scheduled Install Day in week. Possible values are: userDefined, everyday, sunday, monday, tuesday, wednesday, thursday, friday, saturday, noScheduledScan. | `userDefined`, `everyday`, `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday`, `noScheduledScan` |
| ScheduledInstallTime | Write | String | Scheduled Install Time during day | - |
| odataType | Write | String | The type of the entity. | `#microsoft.graph.windowsUpdateActiveHoursInstall`, `#microsoft.graph.windowsUpdateScheduledInstall` |

### Permissions

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, DeviceManagementConfiguration.Read.All |
| Update | Group.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## Related content

- [Overview of the Tenant Configuration Management APIs](https://learn.microsoft.com/en-us/graph/unified-tenant-configuration-management-concept-overview)
- [Set up authentication for TCM](https://learn.microsoft.com/en-us/graph/utcm-authentication-setup)
