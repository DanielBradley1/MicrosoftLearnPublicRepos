<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-04-16 -->

# managedDevice resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Devices that are managed or pre-enrolled through Intune

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedDevices](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-list?view=graph-rest-1.0) | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-1.0) collection | List properties and relationships of the [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-1.0) objects. |
| [Get managedDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-get?view=graph-rest-1.0) | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-1.0) | Read properties and relationships of the [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-1.0) object. |
| [Create managedDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-create?view=graph-rest-1.0) | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-1.0) | Create a new [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-1.0) object. |
| [Delete managedDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-delete?view=graph-rest-1.0) | None | Deletes a [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-1.0). |
| [Update managedDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-update?view=graph-rest-1.0) | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-1.0) | Update the properties of a [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-1.0) object. |
| [Retire action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-retire?view=graph-rest-1.0) | None | Retire a device |
| [Wipe action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-wipe?view=graph-rest-1.0) | None | Wipe a device |
| [resetPasscode action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-resetpasscode?view=graph-rest-1.0) | None | Reset passcode |
| [remoteLock action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-remotelock?view=graph-rest-1.0) | None | Remote lock |
| [requestRemoteAssistance action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-requestremoteassistance?view=graph-rest-1.0) | None | Request remote assistance |
| [disableLostMode action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-disablelostmode?view=graph-rest-1.0) | None | Disable lost mode |
| [locateDevice action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-locatedevice?view=graph-rest-1.0) | None | Locate a device |
| [bypassActivationLock action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-bypassactivationlock?view=graph-rest-1.0) | None | Bypass activation lock |
| [rebootNow action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-rebootnow?view=graph-rest-1.0) | None | Reboot device |
| [shutDown action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-shutdown?view=graph-rest-1.0) | None | Shut down device |
| [recoverPasscode action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-recoverpasscode?view=graph-rest-1.0) | None | Recover passcode |
| [cleanWindowsDevice action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-cleanwindowsdevice?view=graph-rest-1.0) | None | Clean Windows device |
| [logoutSharedAppleDeviceActiveUser action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-logoutsharedappledeviceactiveuser?view=graph-rest-1.0) | None | Logout shared Apple device active user |
| [deleteUserFromSharedAppleDevice action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-deleteuserfromsharedappledevice?view=graph-rest-1.0) | None | Delete user from shared Apple device |
| [syncDevice action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-syncdevice?view=graph-rest-1.0) | None |  |
| [windowsDefenderScan action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-windowsdefenderscan?view=graph-rest-1.0) | None |  |
| [windowsDefenderUpdateSignatures action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-windowsdefenderupdatesignatures?view=graph-rest-1.0) | None |  |
| [updateWindowsDeviceAccount action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-updatewindowsdeviceaccount?view=graph-rest-1.0) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the device. This property is read-only. |
| userId | String | Unique Identifier for the user associated with the device. This property is read-only. |
| deviceName | String | Name of the device. This property is read-only. |
| managedDeviceOwnerType | [managedDeviceOwnerType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceownertype?view=graph-rest-1.0) | Ownership of the device. Can be 'company' or 'personal'. The possible values are: `unknown`, `company`, `personal`. |
| deviceActionResults | [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-1.0) collection | List of ComplexType deviceActionResult objects. This property is read-only. |
| enrolledDateTime | DateTimeOffset | Enrollment time of the device. Supports $filter operator 'lt' and 'gt'. This property is read-only. |
| lastSyncDateTime | DateTimeOffset | The date and time that the device last completed a successful sync with Intune. Supports $filter operator 'lt' and 'gt'. This property is read-only. |
| operatingSystem | String | Operating system of the device. Windows, iOS, etc. This property is read-only. |
| complianceState | [complianceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-compliancestate?view=graph-rest-1.0) | Compliance state of the device. Examples: Compliant, Conflict, Error, etc. Default is unknown. Supports $filter operator 'eq' and 'or'. This property is read-only. The possible values are: `unknown`, `compliant`, `noncompliant`, `conflict`, `error`, `inGracePeriod`, `configManager`. |
| jailBroken | String | Whether the device is jail broken or rooted. Default is an empty string. Supports $filter operator 'eq' and 'or'. This property is read-only. |
| managementAgent | [managementAgentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-managementagenttype?view=graph-rest-1.0) | Management channel of the device. Examples: Intune, EAS, etc. Default is unknown. Supports $filter operator 'eq' and 'or'. This property is read-only. The possible values are: `eas`, `mdm`, `easMdm`, `intuneClient`, `easIntuneClient`, `configurationManagerClient`, `configurationManagerClientMdm`, `configurationManagerClientMdmEas`, `unknown`, `jamf`, `googleCloudDevicePolicyController`. |
| osVersion | String | Operating system version of the device. This property is read-only. |
| easActivated | Boolean | Whether the device is Exchange ActiveSync activated. This property is read-only. |
| easDeviceId | String | Exchange ActiveSync Id of the device. This property is read-only. |
| easActivationDateTime | DateTimeOffset | Exchange ActivationSync activation time of the device. This property is read-only. |
| azureADRegistered | Boolean | Whether the device is Azure Active Directory registered. This property is read-only. |
| deviceEnrollmentType | [deviceEnrollmentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceenrollmenttype.md?view=graph-rest-1.0) | Enrollment type of the device. This property is read-only. The possible values are: `unknown`, `userEnrollment`, `deviceEnrollmentManager`, `appleBulkWithUser`, `appleBulkWithoutUser`, `windowsAzureADJoin`, `windowsBulkUserless`, `windowsAutoEnrollment`, `windowsBulkAzureDomainJoin`, `windowsCoManagement`, `windowsAzureADJoinUsingDeviceAuth`, `appleUserEnrollment`, `appleUserEnrollmentWithServiceAccount`. |
| activationLockBypassCode | String | The code that allows the Activation Lock on managed device to be bypassed. Default, is Null \(Non-Default property\) for this property when returned as part of managedDevice entity in LIST call. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Read-only. This property is read-only. |
| emailAddress | String | Email\(s\) for the user associated with the device. This property is read-only. |
| azureADDeviceId | String | The unique identifier for the Azure Active Directory device. Read only. This property is read-only. |
| deviceRegistrationState | [deviceRegistrationState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceregistrationstate?view=graph-rest-1.0) | Device registration state. This property is read-only. The possible values are: `notRegistered`, `registered`, `revoked`, `keyConflict`, `approvalPending`, `certificateReset`, `notRegisteredPendingEnrollment`, `unknown`. |
| deviceCategoryDisplayName | String | Device category display name. Default is an empty string. Supports $filter operator 'eq' and 'or'. This property is read-only. |
| isSupervised | Boolean | Device supervised status. This property is read-only. |
| exchangeLastSuccessfulSyncDateTime | DateTimeOffset | Last time the device contacted Exchange. This property is read-only. |
| exchangeAccessState | [deviceManagementExchangeAccessState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementexchangeaccessstate?view=graph-rest-1.0) | The Access State of the device in Exchange. This property is read-only. The possible values are: `none`, `unknown`, `allowed`, `blocked`, `quarantined`. |
| exchangeAccessStateReason | [deviceManagementExchangeAccessStateReason](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementexchangeaccessstatereason?view=graph-rest-1.0) | The reason for the device's access state in Exchange. This property is read-only. The possible values are: `none`, `unknown`, `exchangeGlobalRule`, `exchangeIndividualRule`, `exchangeDeviceRule`, `exchangeUpgrade`, `exchangeMailboxPolicy`, `other`, `compliant`, `notCompliant`, `notEnrolled`, `unknownLocation`, `mfaRequired`, `azureADBlockDueToAccessPolicy`, `compromisedPassword`, `deviceNotKnownWithManagedApp`. |
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
| configurationManagerClientEnabledFeatures | [configurationManagerClientEnabledFeatures](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanagerclientenabledfeatures?view=graph-rest-1.0) | ConfigrMgr client enabled features. This property is read-only. |
| wiFiMacAddress | String | Wi-Fi MAC. This property is read-only. |
| deviceHealthAttestationState | [deviceHealthAttestationState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthattestationstate?view=graph-rest-1.0) | The device health attestation state. This property is read-only. |
| subscriberCarrier | String | Subscriber Carrier. This property is read-only. |
| meid | String | MEID. This property is read-only. |
| totalStorageSpaceInBytes | Int64 | Total Storage in Bytes. This property is read-only. |
| freeStorageSpaceInBytes | Int64 | Free Storage in Bytes. Default value is 0. Read-only. This property is read-only. |
| managedDeviceName | String | Automatically generated name to identify a device. Can be overwritten to a user friendly name. |
| partnerReportedThreatState | [managedDevicePartnerReportedHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicepartnerreportedhealthstate?view=graph-rest-1.0) | Indicates the threat state of a device when a Mobile Threat Defense partner is in use by the account and device. Read Only. This property is read-only. The possible values are: `unknown`, `activated`, `deactivated`, `secured`, `lowSeverity`, `mediumSeverity`, `highSeverity`, `unresponsive`, `compromised`, `misconfigured`. |
| requireUserEnrollmentApproval | Boolean | Reports if the managed iOS device is user approval enrollment. This property is read-only. |
| managementCertificateExpirationDate | DateTimeOffset | Reports device management certificate expiration date. This property is read-only. |
| iccid | String | Integrated Circuit Card Identifier, it is A SIM card's unique identification number. Default is an empty string. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Read-only. This property is read-only. |
| udid | String | Unique Device Identifier for iOS and macOS devices. Default is an empty string. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. Read-only. This property is read-only. |
| notes | String | Notes on the device created by IT Admin. Default is null. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. $Search is not supported. |
| ethernetMacAddress | String | Indicates Ethernet MAC Address of the device. Default, is Null \(Non-Default property\) for this property when returned as part of managedDevice entity. Individual get call with select query options is needed to retrieve actual values. Example: deviceManagement/managedDevices\({managedDeviceId}\)?$select=ethernetMacAddress Supports: $select. $Search is not supported. Read-only. This property is read-only. |
| physicalMemoryInBytes | Int64 | Total Memory in Bytes. Default is 0. To retrieve actual values GET call needs to be made, with device id and included in select parameter. Supports: $select. Read-only. This property is read-only. |
| enrollmentProfileName | String | Name of the enrollment profile assigned to the device. Default value is empty string, indicating no enrollment profile was assgined. This property is read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deviceCategory | [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecategory?view=graph-rest-1.0) | Device category |
| windowsProtectionState | [windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsprotectionstate?view=graph-rest-1.0) | The device protection status. This property is read-only. |
| users | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-user?view=graph-rest-1.0) collection | The primary users associated with the managed device. |
| logCollectionRequests | [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) collection | List of log collection requests |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDevice",
  "id": "String (identifier)",
  "userId": "String",
  "deviceName": "String",
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
  "enrolledDateTime": "String (timestamp)",
  "lastSyncDateTime": "String (timestamp)",
  "operatingSystem": "String",
  "complianceState": "String",
  "jailBroken": "String",
  "managementAgent": "String",
  "osVersion": "String",
  "easActivated": true,
  "easDeviceId": "String",
  "easActivationDateTime": "String (timestamp)",
  "azureADRegistered": true,
  "deviceEnrollmentType": "String",
  "activationLockBypassCode": "String",
  "emailAddress": "String",
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
    "windowsUpdateForBusiness": true
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
    "healthAttestationSupportedStatus": "String"
  },
  "subscriberCarrier": "String",
  "meid": "String",
  "totalStorageSpaceInBytes": 1024,
  "freeStorageSpaceInBytes": 1024,
  "managedDeviceName": "String",
  "partnerReportedThreatState": "String",
  "requireUserEnrollmentApproval": true,
  "managementCertificateExpirationDate": "String (timestamp)",
  "iccid": "String",
  "udid": "String",
  "notes": "String",
  "ethernetMacAddress": "String",
  "physicalMemoryInBytes": 1024,
  "enrollmentProfileName": "String"
}
```
