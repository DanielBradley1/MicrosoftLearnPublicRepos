<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-manageddevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-03-18 -->

# managedDevice resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Devices that are managed or pre-enrolled through Intune

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get managedDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-get?view=graph-rest-beta) | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) | Read properties and relationships of the [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) object. |
| [Update managedDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-update?view=graph-rest-beta) | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) | Update the properties of a [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) object. |
| [executeAction action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-executeaction?view=graph-rest-beta) | [bulkManagedDeviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-bulkmanageddeviceactionresult?view=graph-rest-beta) |  |
| [enableLostMode action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-enablelostmode?view=graph-rest-beta) | None | Enable lost mode |
| [playLostModeSound action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-playlostmodesound?view=graph-rest-beta) | None | Play lost mode sound |
| [setDeviceName action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-setdevicename?view=graph-rest-beta) | None | Set device name of the device. |
| [activateDeviceEsim action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-activatedeviceesim?view=graph-rest-beta) | None | Activate eSIM on the device. |
| [rotateFileVaultKey action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-rotatefilevaultkey?view=graph-rest-beta) | None |  |
| [getFileVaultKey function](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-getfilevaultkey?view=graph-rest-beta) | String |  |
| [createDeviceLogCollectionRequest action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-createdevicelogcollectionrequest?view=graph-rest-beta) | [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-beta) |  |
| [retire action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-retire?view=graph-rest-beta) | None | Retire a device |
| [wipe action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-wipe?view=graph-rest-beta) | None | Wipe a device |
| [resetPasscode action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-resetpasscode?view=graph-rest-beta) | None | Reset passcode |
| [remoteLock action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-remotelock?view=graph-rest-beta) | None | Remote lock |
| [requestRemoteAssistance action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-requestremoteassistance?view=graph-rest-beta) | None | Request remote assistance |
| [disableLostMode action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-disablelostmode?view=graph-rest-beta) | None | Disable lost mode |
| [locateDevice action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-locatedevice?view=graph-rest-beta) | None | Locate a device |
| [bypassActivationLock action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-bypassactivationlock?view=graph-rest-beta) | None | Bypass activation lock |
| [rebootNow action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-rebootnow?view=graph-rest-beta) | None | Reboot device |
| [shutDown action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-shutdown?view=graph-rest-beta) | None | Shut down device |
| [recoverPasscode action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-recoverpasscode?view=graph-rest-beta) | None | Recover passcode |
| [cleanWindowsDevice action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-cleanwindowsdevice?view=graph-rest-beta) | None | Clean Windows device |
| [logoutSharedAppleDeviceActiveUser action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-logoutsharedappledeviceactiveuser?view=graph-rest-beta) | None | Logout shared Apple device active user |
| [deleteUserFromSharedAppleDevice action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-deleteuserfromsharedappledevice?view=graph-rest-beta) | None | Delete user from shared Apple device |
| [syncDevice action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-syncdevice?view=graph-rest-beta) | None |  |
| [windowsDefenderScan action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-windowsdefenderscan?view=graph-rest-beta) | None |  |
| [windowsDefenderUpdateSignatures action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-windowsdefenderupdatesignatures?view=graph-rest-beta) | None |  |
| [updateWindowsDeviceAccount action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-updatewindowsdeviceaccount?view=graph-rest-beta) | None |  |
| [revokeAppleVppLicenses action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-revokeapplevpplicenses?view=graph-rest-beta) | None | Revoke all Apple Vpp licenses for a device |
| [rotateBitLockerKeys action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-rotatebitlockerkeys?view=graph-rest-beta) | None | Rotate BitLockerKeys |
| [sendCustomNotificationToCompanyPortal action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-sendcustomnotificationtocompanyportal?view=graph-rest-beta) | None |  |
| [triggerConfigurationManagerAction action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-triggerconfigurationmanageraction?view=graph-rest-beta) | None | Trigger action on ConfigurationManager client |
| [enrollNowAction action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-enrollnowaction?view=graph-rest-beta) | None | Trigger comanagement enrollment action on ConfigurationManager client |
| [deprovision action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-deprovision?view=graph-rest-beta) | None |  |
| [disable action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-disable?view=graph-rest-beta) | None |  |
| [reenable action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-reenable?view=graph-rest-beta) | None |  |
| [moveDevicesToOU action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-movedevicestoou?view=graph-rest-beta) | None |  |
| [removeDeviceFirmwareConfigurationInterfaceManagement action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-removedevicefirmwareconfigurationinterfacemanagement?view=graph-rest-beta) | None | Remove device from Device Firmware Configuration Interface management |
| [initiateMobileDeviceManagementKeyRecovery action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-initiatemobiledevicemanagementkeyrecovery?view=graph-rest-beta) | None | Perform MDM key recovery and TPM attestation |
| [initiateDeviceAttestation action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-initiatedeviceattestation?view=graph-rest-beta) | None | Perform Device Attestation |
| [initiateOnDemandProactiveRemediation action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-initiateondemandproactiveremediation?view=graph-rest-beta) | None | Perform On Demand Proactive Remediation |
| [rotateLocalAdminPassword action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-rotatelocaladminpassword?view=graph-rest-beta) | None | Initiates a manual rotation for the local admin password on the device |
| [pauseConfigurationRefresh action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-pauseconfigurationrefresh?view=graph-rest-beta) | None | Initiates a command to pause config refresh for the device. |
| [changeAssignments action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-changeassignments?view=graph-rest-beta) | None |  |
| [appDiagnostics function](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-appdiagnostics?view=graph-rest-beta) | [powerliftIncidentMetadata](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-powerliftincidentmetadata?view=graph-rest-beta) collection |  |
| [downloadAppDiagnostics action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-downloadappdiagnostics?view=graph-rest-beta) | Stream |  |
| [createQuery action](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-manageddevice-createquery.md?view=graph-rest-beta) | [deviceQueryResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicequeryresult.md?view=graph-rest-beta) | Allows user to send Intune Pivot device query to a managed device |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the device. This property is read-only. |
| userId | String | Unique Identifier for the user associated with the device. This property is read-only. |
| deviceName | String | Name of the device. Supports $filter operator 'eq' and 'contains'. This property is read-only. |
| hardwareInformation | [hardwareInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-hardwareinformation?view=graph-rest-beta) | The hardward details for the device. Includes information such as storage space, manufacturer, serial number, etc. By default most property of this type are set to null/0/false and enum defaults for associated types. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Read-only. This property is read-only. |
| ownerType | [ownerType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ownertype?view=graph-rest-beta) | Ownership of the device. Possible values are, 'company' or 'personal'. Default is unknown. Supports $filter operator 'eq' and 'or'. The possible values are: `unknown`, `company`, `personal`. |
| managedDeviceOwnerType | [managedDeviceOwnerType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-manageddeviceownertype?view=graph-rest-beta) | Ownership of the device. Can be 'company' or 'personal'. The possible values are: `unknown`, `company`, `personal`. |
| deviceActionResults | [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta) collection | List of ComplexType deviceActionResult objects. This property is read-only. |
| managementState | [managementState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-managementstate?view=graph-rest-beta) | Management state of the device. Examples: Managed, RetirePending, etc. Default is managed. Supports $filter operator 'eq' and 'or'. This property is read-only. The possible values are: `managed`, `retirePending`, `retireFailed`, `wipePending`, `wipeFailed`, `unhealthy`, `deletePending`, `retireIssued`, `wipeIssued`, `wipeCanceled`, `retireCanceled`, `discovered`. |
| enrolledDateTime | DateTimeOffset | Enrollment time of the device. Supports $filter operator 'lt' and 'gt'. This property is read-only. |
| lastSyncDateTime | DateTimeOffset | The date and time that the device last completed a successful sync with Intune. Supports $filter operator 'lt' and 'gt'. This property is read-only. |
| chassisType | [chassisType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-chassistype?view=graph-rest-beta) | Chassis type of the device. This property is read-only. The possible values are: `unknown`, `desktop`, `laptop`, `worksWorkstation`, `enterpriseServer`, `phone`, `tablet`, `mobileOther`, `mobileUnknown`. |
| operatingSystem | String | Operating system of the device. Windows, iOS, etc. This property is read-only. |
| deviceType | [deviceType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicetype?view=graph-rest-beta) | Platform of the device. Examples: Desktop, WindowsRT, etc. Default is unknown. Supports $filter operator 'eq' and 'or'. This property is read-only. The possible values are: `desktop`, `windowsRT`, `winMO6`, `nokia`, `windowsPhone`, `mac`, `winCE`, `winEmbedded`, `iPhone`, `iPad`, `iPod`, `android`, `iSocConsumer`, `unix`, `macMDM`, `holoLens`, `surfaceHub`, `androidForWork`, `androidEnterprise`, `windows10x`, `androidnGMS`, `chromeOS`, `linux`, `blackberry`, `palm`, `unknown`, `cloudPC`. |
| complianceState | [complianceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-compliancestate?view=graph-rest-beta) | Compliance state of the device. Examples: Compliant, Conflict, Error, etc. Default is unknown. Supports $filter operator 'eq' and 'or'. This property is read-only. The possible values are: `unknown`, `compliant`, `noncompliant`, `conflict`, `error`, `inGracePeriod`, `configManager`. |
| jailBroken | String | Whether the device is jail broken or rooted. Default is an empty string. Supports $filter operator 'eq' and 'or'. This property is read-only. |
| managementAgent | [managementAgentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-managementagenttype?view=graph-rest-beta) | Management channel of the device. Examples: Intune, EAS, etc. Default is unknown. Supports $filter operator 'eq' and 'or'. This property is read-only. The possible values are: `eas`, `mdm`, `easMdm`, `intuneClient`, `easIntuneClient`, `configurationManagerClient`, `configurationManagerClientMdm`, `configurationManagerClientMdmEas`, `unknown`, `jamf`, `googleCloudDevicePolicyController`, `microsoft365ManagedMdm`, `msSense`, `intuneAosp`, `google`, `unknownFutureValue`. |
| osVersion | String | Operating system version of the device. This property is read-only. |
| easActivated | Boolean | Whether the device is Exchange ActiveSync activated. This property is read-only. |
| easDeviceId | String | Exchange ActiveSync Id of the device. This property is read-only. |
| easActivationDateTime | DateTimeOffset | Exchange ActivationSync activation time of the device. This property is read-only. |
| aadRegistered | Boolean | Whether the device is Azure Active Directory registered. This property is read-only. |
| azureADRegistered | Boolean | Whether the device is Azure Active Directory registered. This property is read-only. |
| deviceEnrollmentType | [deviceEnrollmentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceenrollmenttype.md?view=graph-rest-beta) | Enrollment type of the device. This property is read-only. The possible values are: `unknown`, `userEnrollment`, `deviceEnrollmentManager`, `appleBulkWithUser`, `appleBulkWithoutUser`, `windowsAzureADJoin`, `windowsBulkUserless`, `windowsAutoEnrollment`, `windowsBulkAzureDomainJoin`, `windowsCoManagement`, `windowsAzureADJoinUsingDeviceAuth`, `appleUserEnrollment`, `appleUserEnrollmentWithServiceAccount`, `azureAdJoinUsingAzureVmExtension`, `androidEnterpriseDedicatedDevice`, `androidEnterpriseFullyManaged`, `androidEnterpriseCorporateWorkProfile`, `androidAOSPUserOwnedDeviceEnrollment`, `androidAOSPUserlessDeviceEnrollment`, `appleACMEBasicBYOD`, `appleACMEDEPUserless`, `appleACMEDEPUDACompanyPortal`, `appleACMEDEPUDASetupAsstLegacy`, `appleACMEDEPUDAModernAuth`. |
| lostModeState | [lostModeState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-lostmodestate?view=graph-rest-beta) | Indicates if Lost mode is enabled or disabled. This property is read-only. The possible values are: `disabled`, `enabled`. |
| activationLockBypassCode | String | The code that allows the Activation Lock on managed device to be bypassed. Default, is Null \(Non-Default property\) for this property when returned as part of managedDevice entity in LIST call. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Read-only. This property is read-only. |
| emailAddress | String | Email\(s\) for the user associated with the device. This property is read-only. |
| azureActiveDirectoryDeviceId | String | The unique identifier for the Azure Active Directory device. Read only. This property is read-only. |
| azureADDeviceId | String | The unique identifier for the Azure Active Directory device. Read only. This property is read-only. |
| deviceRegistrationState | [deviceRegistrationState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceregistrationstate?view=graph-rest-beta) | Device registration state. This property is read-only. The possible values are: `notRegistered`, `registered`, `revoked`, `keyConflict`, `approvalPending`, `certificateReset`, `notRegisteredPendingEnrollment`, `unknown`. |
| deviceCategoryDisplayName | String | Device category display name. Default is an empty string. Supports $filter operator 'eq' and 'or'. This property is read-only. |
| isSupervised | Boolean | Device supervised status. This property is read-only. |
| exchangeLastSuccessfulSyncDateTime | DateTimeOffset | Last time the device contacted Exchange. This property is read-only. |
| exchangeAccessState | [deviceManagementExchangeAccessState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementexchangeaccessstate?view=graph-rest-beta) | The Access State of the device in Exchange. This property is read-only. The possible values are: `none`, `unknown`, `allowed`, `blocked`, `quarantined`. |
| exchangeAccessStateReason | [deviceManagementExchangeAccessStateReason](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementexchangeaccessstatereason?view=graph-rest-beta) | The reason for the device's access state in Exchange. This property is read-only. The possible values are: `none`, `unknown`, `exchangeGlobalRule`, `exchangeIndividualRule`, `exchangeDeviceRule`, `exchangeUpgrade`, `exchangeMailboxPolicy`, `other`, `compliant`, `notCompliant`, `notEnrolled`, `unknownLocation`, `mfaRequired`, `azureADBlockDueToAccessPolicy`, `compromisedPassword`, `deviceNotKnownWithManagedApp`. |
| remoteAssistanceSessionUrl | String | Url that allows a Remote Assistance session to be established with the device. Default is an empty string. To retrieve actual values GET call needs to be made, with device id and included in select parameter. This property is read-only. |
| remoteAssistanceSessionErrorDetails | String | An error string that identifies issues when creating Remote Assistance session objects. This property is read-only. |
| isEncrypted | Boolean | Device encryption status. This property is read-only. |
| userPrincipalName | String | Device user principal name. This property is read-only. |
| model | String | Model of the device. This property is read-only. |
| manufacturer | String | Manufacturer of the device. This property is read-only. |
| imei | String | IMEI. This property is read-only. |
| complianceGracePeriodExpirationDateTime | DateTimeOffset | The DateTime when device compliance grace period expires. This property is read-only. |
| serialNumber | String | SerialNumber. This property is read-only. |
| phoneNumber | String | Phone number of the device. This property is read-only. |
| androidSecurityPatchLevel | String | Android security patch level. This property is read-only. |
| userDisplayName | String | User display name. This property is read-only. |
| configurationManagerClientEnabledFeatures | [configurationManagerClientEnabledFeatures](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanagerclientenabledfeatures?view=graph-rest-beta) | ConfigrMgr client enabled features. This property is read-only. |
| wiFiMacAddress | String | Wi-Fi MAC. This property is read-only. |
| deviceHealthAttestationState | [deviceHealthAttestationState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthattestationstate?view=graph-rest-beta) | The device health attestation state. This property is read-only. |
| subscriberCarrier | String | Subscriber Carrier. This property is read-only. |
| meid | String | MEID. This property is read-only. |
| totalStorageSpaceInBytes | Int64 | Total Storage in Bytes. This property is read-only. |
| freeStorageSpaceInBytes | Int64 | Free Storage in Bytes. Default value is 0. Read-only. This property is read-only. |
| managedDeviceName | String | Automatically generated name to identify a device. Can be overwritten to a user friendly name. |
| partnerReportedThreatState | [managedDevicePartnerReportedHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicepartnerreportedhealthstate?view=graph-rest-beta) | Indicates the threat state of a device when a Mobile Threat Defense partner is in use by the account and device. Read Only. This property is read-only. The possible values are: `unknown`, `activated`, `deactivated`, `secured`, `lowSeverity`, `mediumSeverity`, `highSeverity`, `unresponsive`, `compromised`, `misconfigured`. |
| retireAfterDateTime | DateTimeOffset | Indicates the time after when a device will be auto retired because of scheduled action. This property is read-only. |
| usersLoggedOn | [loggedOnUser](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-loggedonuser?view=graph-rest-beta) collection | Indicates the last logged on users of a device. This property is read-only. |
| preferMdmOverGroupPolicyAppliedDateTime | DateTimeOffset | Reports the DateTime the preferMdmOverGroupPolicy setting was set. When set, the Intune MDM settings will override Group Policy settings if there is a conflict. Read Only. This property is read-only. |
| autopilotEnrolled | Boolean | Reports if the managed device is enrolled via auto-pilot. This property is read-only. |
| requireUserEnrollmentApproval | Boolean | Reports if the managed iOS device is user approval enrollment. This property is read-only. |
| managementCertificateExpirationDate | DateTimeOffset | Reports device management certificate expiration date. This property is read-only. |
| iccid | String | Integrated Circuit Card Identifier, it is A SIM card's unique identification number. Default is an empty string. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Read-only. This property is read-only. |
| udid | String | Unique Device Identifier for iOS and macOS devices. Default is an empty string. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Read-only. This property is read-only. |
| roleScopeTagIds | String collection | List of Scope Tag IDs for this Device instance. |
| windowsActiveMalwareCount | Int32 | Count of active malware for this windows device. Default is 0. To retrieve actual values GET call needs to be made, with device id and included in select parameter. This property is read-only. |
| windowsRemediatedMalwareCount | Int32 | Count of remediated malware for this windows device. Default is 0. To retrieve actual values GET call needs to be made, with device id and included in select parameter. This property is read-only. |
| notes | String | Notes on the device created by IT Admin. Default is null. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. |
| configurationManagerClientHealthState | [configurationManagerClientHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanagerclienthealthstate?view=graph-rest-beta) | Configuration manager client health state, valid only for devices managed by MDM/ConfigMgr Agent |
| configurationManagerClientInformation | [configurationManagerClientInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanagerclientinformation?view=graph-rest-beta) | Configuration manager client information, valid only for devices managed, duel-managed or tri-managed by ConfigMgr Agent |
| ethernetMacAddress | String | Indicates Ethernet MAC Address of the device. Default, is Null \(Non-Default property\) for this property when returned as part of managedDevice entity. Individual get call with select query options is needed to retrieve actual values. Example: deviceManagement/managedDevices\({managedDeviceId}\)?$select=ethernetMacAddress Supports: $select. $Search is not supported. Read-only. This property is read-only. |
| physicalMemoryInBytes | Int64 | Total Memory in Bytes. Default is 0. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. Read-only. This property is read-only. |
| processorArchitecture | [managedDeviceArchitecture](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-manageddevicearchitecture?view=graph-rest-beta) | Processor architecture. This property is read-only. The possible values are: `unknown`, `x86`, `x64`, `arm`, `arM64`. |
| specificationVersion | String | Specification version. This property is read-only. |
| joinType | [joinType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-jointype?view=graph-rest-beta) | Device join type. The possible values are: `unknown`, `azureADJoined`, `azureADRegistered`, `hybridAzureADJoined`. |
| skuFamily | String | Device sku family |
| securityPatchLevel | String | This indicates the security patch level of the operating system. These special updates contain important security fixes. For iOS/MacOS they are in \(a\) format. For android its in 2017-08-07 format. This property is read-only. |
| skuNumber | Int32 | Device sku number, see also: [https://learn.microsoft.com/windows/win32/api/sysinfoapi/nf-sysinfoapi-getproductinfo](https://learn.microsoft.com/en-us/windows/win32/api/sysinfoapi/nf-sysinfoapi-getproductinfo). Valid values 0 to 2147483647. This property is read-only. |
| managementFeatures | [managedDeviceManagementFeatures](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicemanagementfeatures?view=graph-rest-beta) | Device management features. The possible values are: `none`, `microsoftManagedDesktop`. |
| chromeOSDeviceInfo | [chromeOSDeviceProperty](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-chromeosdeviceproperty?view=graph-rest-beta) collection | List of properties of the ChromeOS Device. Default is an empty list. To retrieve actual values GET call needs to be made, with device id and included in select parameter. |
| enrollmentProfileName | String | Name of the enrollment profile assigned to the device. Default value is empty string, indicating no enrollment profile was assgined. This property is read-only. |
| bootstrapTokenEscrowed | Boolean | Reports if the managed device has an escrowed Bootstrap Token. This is only for macOS devices. To get, include BootstrapTokenEscrowed in the select clause and query with a device id. If FALSE, no bootstrap token is escrowed. If TRUE, the device has escrowed a bootstrap token with Intune. This property is read-only. |
| deviceFirmwareConfigurationInterfaceManaged | Boolean | Indicates whether the device is DFCI managed. When TRUE the device is DFCI managed. When FALSE, the device is not DFCI managed. The default value is FALSE. |
| deviceIdentityAttestationDetail | [deviceIdentityAttestationDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceidentityattestationdetail?view=graph-rest-beta) | Indicates the attestation status of the managed device. And in which way. Default: Unknown. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| detectedApps | [detectedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-detectedapp?view=graph-rest-beta) collection | All applications currently installed on the device |
| deviceCategory | [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta) | Device category |
| windowsProtectionState | [windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsprotectionstate?view=graph-rest-beta) | The device protection status. This property is read-only. |
| users | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) collection | The primary users associated with the managed device. |
| logCollectionRequests | [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-beta) collection | List of log collection requests |
| deviceHealthScriptStates | [deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta) collection | Results of device health scripts that ran for this device. Default is empty list. This property is read-only. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDevice",
  "id": "String (identifier)",
  "userId": "String",
  "deviceName": "String",
  "hardwareInformation": {
    "@odata.type": "microsoft.graph.hardwareInformation",
    "serialNumber": "String",
    "totalStorageSpace": 1024,
    "freeStorageSpace": 1024,
    "imei": "String",
    "meid": "String",
    "manufacturer": "String",
    "model": "String",
    "phoneNumber": "String",
    "subscriberCarrier": "String",
    "cellularTechnology": "String",
    "wifiMac": "String",
    "operatingSystemLanguage": "String",
    "isSupervised": true,
    "isEncrypted": true,
    "batterySerialNumber": "String",
    "batteryHealthPercentage": 1024,
    "batteryChargeCycles": 1024,
    "isSharedDevice": true,
    "sharedDeviceCachedUsers": [
      {
        "@odata.type": "microsoft.graph.sharedAppleDeviceUser",
        "userPrincipalName": "String",
        "dataToSync": true,
        "dataQuota": 1024,
        "dataUsed": 1024
      }
    ],
    "tpmSpecificationVersion": "String",
    "operatingSystemEdition": "String",
    "deviceFullQualifiedDomainName": "String",
    "deviceGuardVirtualizationBasedSecurityHardwareRequirementState": "String",
    "deviceGuardVirtualizationBasedSecurityState": "String",
    "deviceGuardLocalSystemAuthorityCredentialGuardState": "String",
    "osBuildNumber": "String",
    "operatingSystemProductType": 1024,
    "ipAddressV4": "String",
    "subnetAddress": "String",
    "esimIdentifier": "String",
    "systemManagementBIOSVersion": "String",
    "tpmManufacturer": "String",
    "tpmVersion": "String",
    "wiredIPv4Addresses": [
      "String"
    ],
    "batteryLevelPercentage": "4.2",
    "residentUsersCount": 1024,
    "productName": "String",
    "deviceLicensingStatus": "String",
    "deviceLicensingLastErrorCode": 1024,
    "deviceLicensingLastErrorDescription": "String"
  },
  "ownerType": "String",
  "managedDeviceOwnerType": "String",
  "deviceActionResults": [
    {
      "@odata.type": "microsoft.graph.deviceActionResult",
      "actionName": "String",
      "actionState": "String",
      "startDateTime": "String (timestamp)",
      "lastUpdatedDateTime": "String (timestamp)"
    }
  ],
  "managementState": "String",
  "enrolledDateTime": "String (timestamp)",
  "lastSyncDateTime": "String (timestamp)",
  "chassisType": "String",
  "operatingSystem": "String",
  "deviceType": "String",
  "complianceState": "String",
  "jailBroken": "String",
  "managementAgent": "String",
  "osVersion": "String",
  "easActivated": true,
  "easDeviceId": "String",
  "easActivationDateTime": "String (timestamp)",
  "aadRegistered": true,
  "azureADRegistered": true,
  "deviceEnrollmentType": "String",
  "lostModeState": "String",
  "activationLockBypassCode": "String",
  "emailAddress": "String",
  "azureActiveDirectoryDeviceId": "String",
  "azureADDeviceId": "String",
  "deviceRegistrationState": "String",
  "deviceCategoryDisplayName": "String",
  "isSupervised": true,
  "exchangeLastSuccessfulSyncDateTime": "String (timestamp)",
  "exchangeAccessState": "String",
  "exchangeAccessStateReason": "String",
  "remoteAssistanceSessionUrl": "String",
  "remoteAssistanceSessionErrorDetails": "String",
  "isEncrypted": true,
  "userPrincipalName": "String",
  "model": "String",
  "manufacturer": "String",
  "imei": "String",
  "complianceGracePeriodExpirationDateTime": "String (timestamp)",
  "serialNumber": "String",
  "phoneNumber": "String",
  "androidSecurityPatchLevel": "String",
  "userDisplayName": "String",
  "configurationManagerClientEnabledFeatures": {
    "@odata.type": "microsoft.graph.configurationManagerClientEnabledFeatures",
    "inventory": true,
    "modernApps": true,
    "resourceAccess": true,
    "deviceConfiguration": true,
    "compliancePolicy": true,
    "windowsUpdateForBusiness": true,
    "endpointProtection": true,
    "officeApps": true
  },
  "wiFiMacAddress": "String",
  "deviceHealthAttestationState": {
    "@odata.type": "microsoft.graph.deviceHealthAttestationState",
    "lastUpdateDateTime": "String",
    "contentNamespaceUrl": "String",
    "deviceHealthAttestationStatus": "String",
    "contentVersion": "String",
    "issuedDateTime": "String (timestamp)",
    "attestationIdentityKey": "String",
    "resetCount": 1024,
    "restartCount": 1024,
    "dataExcutionPolicy": "String",
    "bitLockerStatus": "String",
    "bootManagerVersion": "String",
    "codeIntegrityCheckVersion": "String",
    "secureBoot": "String",
    "bootDebugging": "String",
    "operatingSystemKernelDebugging": "String",
    "codeIntegrity": "String",
    "testSigning": "String",
    "safeMode": "String",
    "windowsPE": "String",
    "earlyLaunchAntiMalwareDriverProtection": "String",
    "virtualSecureMode": "String",
    "pcrHashAlgorithm": "String",
    "bootAppSecurityVersion": "String",
    "bootManagerSecurityVersion": "String",
    "tpmVersion": "String",
    "pcr0": "String",
    "secureBootConfigurationPolicyFingerPrint": "String",
    "codeIntegrityPolicy": "String",
    "bootRevisionListInfo": "String",
    "operatingSystemRevListInfo": "String",
    "healthStatusMismatchInfo": "String",
    "healthAttestationSupportedStatus": "String",
    "memoryIntegrityProtection": "String",
    "memoryAccessProtection": "String",
    "virtualizationBasedSecurity": "String",
    "firmwareProtection": "String",
    "systemManagementMode": "String",
    "securedCorePC": "String"
  },
  "subscriberCarrier": "String",
  "meid": "String",
  "totalStorageSpaceInBytes": 1024,
  "freeStorageSpaceInBytes": 1024,
  "managedDeviceName": "String",
  "partnerReportedThreatState": "String",
  "retireAfterDateTime": "String (timestamp)",
  "usersLoggedOn": [
    {
      "@odata.type": "microsoft.graph.loggedOnUser",
      "userId": "String",
      "lastLogOnDateTime": "String (timestamp)"
    }
  ],
  "preferMdmOverGroupPolicyAppliedDateTime": "String (timestamp)",
  "autopilotEnrolled": true,
  "requireUserEnrollmentApproval": true,
  "managementCertificateExpirationDate": "String (timestamp)",
  "iccid": "String",
  "udid": "String",
  "roleScopeTagIds": [
    "String"
  ],
  "windowsActiveMalwareCount": 1024,
  "windowsRemediatedMalwareCount": 1024,
  "notes": "String",
  "configurationManagerClientHealthState": {
    "@odata.type": "microsoft.graph.configurationManagerClientHealthState",
    "state": "String",
    "errorCode": 1024,
    "lastSyncDateTime": "String (timestamp)"
  },
  "configurationManagerClientInformation": {
    "@odata.type": "microsoft.graph.configurationManagerClientInformation",
    "clientIdentifier": "String",
    "isBlocked": true,
    "clientVersion": "String"
  },
  "ethernetMacAddress": "String",
  "physicalMemoryInBytes": 1024,
  "processorArchitecture": "String",
  "specificationVersion": "String",
  "joinType": "String",
  "skuFamily": "String",
  "securityPatchLevel": "String",
  "skuNumber": 1024,
  "managementFeatures": "String",
  "chromeOSDeviceInfo": [
    {
      "@odata.type": "microsoft.graph.chromeOSDeviceProperty",
      "name": "String",
      "value": "String",
      "valueType": "String",
      "updatable": true
    }
  ],
  "enrollmentProfileName": "String",
  "bootstrapTokenEscrowed": true,
  "deviceFirmwareConfigurationInterfaceManaged": true,
  "deviceIdentityAttestationDetail": {
    "@odata.type": "microsoft.graph.deviceIdentityAttestationDetail",
    "deviceIdentityAttestationStatus": "String"
  }
}
```
