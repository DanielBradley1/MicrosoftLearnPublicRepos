<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanageddevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# windowsManagedDevice resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows devices that are managed or pre-enrolled through Intune

Inherits from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsManagedDevices](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanageddevice-list?view=graph-rest-beta) | [windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanageddevice?view=graph-rest-beta) collection | List properties and relationships of the [windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanageddevice?view=graph-rest-beta) objects. |
| [Get windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanageddevice-get?view=graph-rest-beta) | [windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanageddevice?view=graph-rest-beta) | Read properties and relationships of the [windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanageddevice?view=graph-rest-beta) object. |
| [Create windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanageddevice-create?view=graph-rest-beta) | [windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanageddevice?view=graph-rest-beta) | Create a new [windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanageddevice?view=graph-rest-beta) object. |
| [Delete windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanageddevice-delete?view=graph-rest-beta) | None | Deletes a [windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanageddevice?view=graph-rest-beta). |
| [Update windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanageddevice-update?view=graph-rest-beta) | [windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanageddevice?view=graph-rest-beta) | Update the properties of a [windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanageddevice?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| userId | String | Unique Identifier for the user associated with the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| deviceName | String | Name of the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| hardwareInformation | [hardwareInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-hardwareinformation?view=graph-rest-beta) | The hardward details for the device. Includes information such as storage space, manufacturer, serial number, etc. By default most property of this type are set to null/0/false and enum defaults for associated types. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Read-only. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| ownerType | [ownerType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ownertype?view=graph-rest-beta) | Ownership of the device. Possible values are, 'company' or 'personal'. Default is unknown. Supports $filter operator 'eq' and 'or'. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `unknown`, `company`, `personal`. |
| managedDeviceOwnerType | [managedDeviceOwnerType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-manageddeviceownertype?view=graph-rest-beta) | Ownership of the device. Can be 'company' or 'personal' Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `unknown`, `company`, `personal`. |
| deviceActionResults | [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta) collection | List of ComplexType deviceActionResult objects. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| managementState | [managementState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-managementstate?view=graph-rest-beta) | Management state of the device. Examples: Managed, RetirePending, etc. Default is managed. Supports $filter operator 'eq' and 'or'. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `managed`, `retirePending`, `retireFailed`, `wipePending`, `wipeFailed`, `unhealthy`, `deletePending`, `retireIssued`, `wipeIssued`, `wipeCanceled`, `retireCanceled`, `discovered`. |
| enrolledDateTime | DateTimeOffset | Enrollment time of the device. Supports $filter operator 'lt' and 'gt'. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| lastSyncDateTime | DateTimeOffset | The date and time that the device last completed a successful sync with Intune. Supports $filter operator 'lt' and 'gt'. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| chassisType | [chassisType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-chassistype?view=graph-rest-beta) | Chassis type of the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `unknown`, `desktop`, `laptop`, `worksWorkstation`, `enterpriseServer`, `phone`, `tablet`, `mobileOther`, `mobileUnknown`. |
| operatingSystem | String | Operating system of the device. Windows, iOS, etc. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| deviceType | [deviceType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicetype?view=graph-rest-beta) | Platform of the device. Examples: Desktop, WindowsRT, etc. Default is unknown. Supports $filter operator 'eq' and 'or'. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `desktop`, `windowsRT`, `winMO6`, `nokia`, `windowsPhone`, `mac`, `winCE`, `winEmbedded`, `iPhone`, `iPad`, `iPod`, `android`, `iSocConsumer`, `unix`, `macMDM`, `holoLens`, `surfaceHub`, `androidForWork`, `androidEnterprise`, `windows10x`, `androidnGMS`, `chromeOS`, `linux`, `blackberry`, `palm`, `unknown`, `cloudPC`. |
| complianceState | [complianceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-compliancestate?view=graph-rest-beta) | Compliance state of the device. Examples: Compliant, Conflict, Error, etc. Default is unknown. Supports $filter operator 'eq' and 'or'. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `unknown`, `compliant`, `noncompliant`, `conflict`, `error`, `inGracePeriod`, `configManager`. |
| jailBroken | String | Whether the device is jail broken or rooted. Default is an empty string. Supports $filter operator 'eq' and 'or'. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| managementAgent | [managementAgentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-managementagenttype?view=graph-rest-beta) | Management channel of the device. Examples: Intune, EAS, etc. Default is unknown. Supports $filter operator 'eq' and 'or'. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `eas`, `mdm`, `easMdm`, `intuneClient`, `easIntuneClient`, `configurationManagerClient`, `configurationManagerClientMdm`, `configurationManagerClientMdmEas`, `unknown`, `jamf`, `googleCloudDevicePolicyController`, `microsoft365ManagedMdm`, `msSense`, `intuneAosp`, `google`, `unknownFutureValue`. |
| osVersion | String | Operating system version of the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| easActivated | Boolean | Whether the device is Exchange ActiveSync activated. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| easDeviceId | String | Exchange ActiveSync Id of the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| easActivationDateTime | DateTimeOffset | Exchange ActivationSync activation time of the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| aadRegistered | Boolean | Whether the device is Azure Active Directory registered. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| azureADRegistered | Boolean | Whether the device is Azure Active Directory registered. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| deviceEnrollmentType | [deviceEnrollmentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceenrollmenttype.md?view=graph-rest-beta) | Enrollment type of the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `unknown`, `userEnrollment`, `deviceEnrollmentManager`, `appleBulkWithUser`, `appleBulkWithoutUser`, `windowsAzureADJoin`, `windowsBulkUserless`, `windowsAutoEnrollment`, `windowsBulkAzureDomainJoin`, `windowsCoManagement`, `windowsAzureADJoinUsingDeviceAuth`, `appleUserEnrollment`, `appleUserEnrollmentWithServiceAccount`, `azureAdJoinUsingAzureVmExtension`, `androidEnterpriseDedicatedDevice`, `androidEnterpriseFullyManaged`, `androidEnterpriseCorporateWorkProfile`, `appleACMEBasicBYOD`, `appleACMEDEPUserless`, `appleACMEDEPUDACompanyPortal`, `appleACMEDEPUDASetupAsstLegacy`, `appleACMEDEPUDAModernAuth`. |
| lostModeState | [lostModeState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-lostmodestate?view=graph-rest-beta) | Indicates if Lost mode is enabled or disabled. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `disabled`, `enabled`. |
| activationLockBypassCode | String | The code that allows the Activation Lock on managed device to be bypassed. Default, is Null \(Non-Default property\) for this property when returned as part of managedDevice entity in LIST call. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Read-only. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| emailAddress | String | Email\(s\) for the user associated with the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| azureActiveDirectoryDeviceId | String | The unique identifier for the Azure Active Directory device. Read only. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| azureADDeviceId | String | The unique identifier for the Azure Active Directory device. Read only. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| deviceRegistrationState | [deviceRegistrationState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceregistrationstate?view=graph-rest-beta) | Device registration state. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `notRegistered`, `registered`, `revoked`, `keyConflict`, `approvalPending`, `certificateReset`, `notRegisteredPendingEnrollment`, `unknown`. |
| deviceCategoryDisplayName | String | Device category display name. Default is an empty string. Supports $filter operator 'eq' and 'or'. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| isSupervised | Boolean | Device supervised status. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| exchangeLastSuccessfulSyncDateTime | DateTimeOffset | Last time the device contacted Exchange. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| exchangeAccessState | [deviceManagementExchangeAccessState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementexchangeaccessstate?view=graph-rest-beta) | The Access State of the device in Exchange. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `none`, `unknown`, `allowed`, `blocked`, `quarantined`. |
| exchangeAccessStateReason | [deviceManagementExchangeAccessStateReason](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementexchangeaccessstatereason?view=graph-rest-beta) | The reason for the device's access state in Exchange. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `none`, `unknown`, `exchangeGlobalRule`, `exchangeIndividualRule`, `exchangeDeviceRule`, `exchangeUpgrade`, `exchangeMailboxPolicy`, `other`, `compliant`, `notCompliant`, `notEnrolled`, `unknownLocation`, `mfaRequired`, `azureADBlockDueToAccessPolicy`, `compromisedPassword`, `deviceNotKnownWithManagedApp`. |
| remoteAssistanceSessionUrl | String | Url that allows a Remote Assistance session to be established with the device. Default is an empty string. To retrieve actual values GET call needs to be made, with device id and included in select parameter. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| remoteAssistanceSessionErrorDetails | String | An error string that identifies issues when creating Remote Assistance session objects. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| isEncrypted | Boolean | Device encryption status. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| userPrincipalName | String | Device user principal name. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| model | String | Model of the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| manufacturer | String | Manufacturer of the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| imei | String | IMEI. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| complianceGracePeriodExpirationDateTime | DateTimeOffset | The DateTime when device compliance grace period expires. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| serialNumber | String | SerialNumber. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| phoneNumber | String | Phone number of the device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| androidSecurityPatchLevel | String | Android security patch level. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| userDisplayName | String | User display name. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| configurationManagerClientEnabledFeatures | [configurationManagerClientEnabledFeatures](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanagerclientenabledfeatures?view=graph-rest-beta) | ConfigrMgr client enabled features. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| wiFiMacAddress | String | Wi-Fi MAC. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| deviceHealthAttestationState | [deviceHealthAttestationState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthattestationstate?view=graph-rest-beta) | The device health attestation state. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| subscriberCarrier | String | Subscriber Carrier. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| meid | String | MEID. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| totalStorageSpaceInBytes | Int64 | Total Storage in Bytes. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| freeStorageSpaceInBytes | Int64 | Free Storage in Bytes. Default value is 0. Read-only. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| managedDeviceName | String | Automatically generated name to identify a device. Can be overwritten to a user friendly name. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| partnerReportedThreatState | [managedDevicePartnerReportedHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicepartnerreportedhealthstate?view=graph-rest-beta) | Indicates the threat state of a device when a Mobile Threat Defense partner is in use by the account and device. Read Only. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `unknown`, `activated`, `deactivated`, `secured`, `lowSeverity`, `mediumSeverity`, `highSeverity`, `unresponsive`, `compromised`, `misconfigured`. |
| retireAfterDateTime | DateTimeOffset | Indicates the time after when a device will be auto retired because of scheduled action. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| usersLoggedOn | [loggedOnUser](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-loggedonuser?view=graph-rest-beta) collection | Indicates the last logged on users of a device. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| preferMdmOverGroupPolicyAppliedDateTime | DateTimeOffset | Reports the DateTime the preferMdmOverGroupPolicy setting was set. When set, the Intune MDM settings will override Group Policy settings if there is a conflict. Read Only. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| autopilotEnrolled | Boolean | Reports if the managed device is enrolled via auto-pilot. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| requireUserEnrollmentApproval | Boolean | Reports if the managed iOS device is user approval enrollment. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| managementCertificateExpirationDate | DateTimeOffset | Reports device management certificate expiration date. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| iccid | String | Integrated Circuit Card Identifier, it is A SIM card's unique identification number. Default is an empty string. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Read-only. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| udid | String | Unique Device Identifier for iOS and macOS devices. Default is an empty string. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Read-only. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of Scope Tag IDs for this Device instance. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| windowsActiveMalwareCount | Int32 | Count of active malware for this windows device. Default is 0. To retrieve actual values GET call needs to be made, with device id and included in select parameter. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| windowsRemediatedMalwareCount | Int32 | Count of remediated malware for this windows device. Default is 0. To retrieve actual values GET call needs to be made, with device id and included in select parameter. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| notes | String | Notes on the device created by IT Admin. Default is null. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| configurationManagerClientHealthState | [configurationManagerClientHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanagerclienthealthstate?view=graph-rest-beta) | Configuration manager client health state, valid only for devices managed by MDM/ConfigMgr Agent Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| configurationManagerClientInformation | [configurationManagerClientInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanagerclientinformation?view=graph-rest-beta) | Configuration manager client information, valid only for devices managed, duel-managed or tri-managed by ConfigMgr Agent Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| ethernetMacAddress | String | Indicates Ethernet MAC Address of the device. Default, is Null \(Non-Default property\) for this property when returned as part of managedDevice entity. Individual get call with select query options is needed to retrieve actual values. Example: deviceManagement/managedDevices\({managedDeviceId}\)?$select=ethernetMacAddress Supports: $select. $Search is not supported. Read-only. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| physicalMemoryInBytes | Int64 | Total Memory in Bytes. Default is 0. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. Read-only. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| processorArchitecture | [managedDeviceArchitecture](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-manageddevicearchitecture?view=graph-rest-beta) | Processor architecture. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `unknown`, `x86`, `x64`, `arm`, `arM64`. |
| specificationVersion | String | Specification version. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| joinType | [joinType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-jointype?view=graph-rest-beta) | Device join type Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `unknown`, `azureADJoined`, `azureADRegistered`, `hybridAzureADJoined`. |
| skuFamily | String | Device sku family Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| securityPatchLevel | String | This indicates the security patch level of the operating system. These special updates contain important security fixes. For iOS/MacOS they are in \(a\) format. For android its in 2017-08-07 format. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| skuNumber | Int32 | Device sku number, see also: [https://learn.microsoft.com/windows/win32/api/sysinfoapi/nf-sysinfoapi-getproductinfo](https://learn.microsoft.com/en-us/windows/win32/api/sysinfoapi/nf-sysinfoapi-getproductinfo). Valid values 0 to 2147483647. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| managementFeatures | [managedDeviceManagementFeatures](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicemanagementfeatures?view=graph-rest-beta) | Device management features Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta). The possible values are: `none`, `microsoftManagedDesktop`. |
| chromeOSDeviceInfo | [chromeOSDeviceProperty](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-chromeosdeviceproperty?view=graph-rest-beta) collection | List of properties of the ChromeOS Device. Default is an empty list. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| enrollmentProfileName | String | Name of the enrollment profile assigned to the device. Default value is empty string, indicating no enrollment profile was assgined. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| bootstrapTokenEscrowed | Boolean | Reports if the managed device has an escrowed Bootstrap Token. This is only for macOS devices. To get, include BootstrapTokenEscrowed in the select clause and query with a device id. If FALSE, no bootstrap token is escrowed. If TRUE, the device has escrowed a bootstrap token with Intune. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| deviceFirmwareConfigurationInterfaceManaged | Boolean | Indicates whether the device is DFCI managed. When TRUE the device is DFCI managed. When FALSE, the device is not DFCI managed. The default value is FALSE. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| deviceIdentityAttestationDetail | [deviceIdentityAttestationDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceidentityattestationdetail?view=graph-rest-beta) | Indicates the attestation status of the managed device. And in which way. Default: Unknown. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| detectedApps | [detectedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-detectedapp?view=graph-rest-beta) collection | All applications currently installed on the device Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| deviceCategory | [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta) | Device category Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| windowsProtectionState | [windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsprotectionstate?view=graph-rest-beta) | The device protection status. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| users | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) collection | The primary users associated with the managed device. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| logCollectionRequests | [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-beta) collection | List of log collection requests Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |
| deviceHealthScriptStates | [deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta) collection | Results of device health scripts that ran for this device. Default is empty list. This property is read-only. Inherited from [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsManagedDevice",
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
