<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# managedDeviceEncryptionState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Encryption report per device

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedDeviceEncryptionStates](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-manageddeviceencryptionstate-list?view=graph-rest-beta) | [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta) collection | List properties and relationships of the [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta) objects. |
| [Get managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-manageddeviceencryptionstate-get?view=graph-rest-beta) | [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta) | Read properties and relationships of the [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta) object. |
| [Create managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-manageddeviceencryptionstate-create?view=graph-rest-beta) | [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta) | Create a new [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta) object. |
| [Delete managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-manageddeviceencryptionstate-delete?view=graph-rest-beta) | None | Deletes a [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta). |
| [Update managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-manageddeviceencryptionstate-update?view=graph-rest-beta) | [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta) | Update the properties of a [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| userPrincipalName | String | User name |
| deviceType | [deviceTypes](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicetypes?view=graph-rest-beta) | Platform of the device. Possible values are: `desktop`, `windowsRT`, `winMO6`, `nokia`, `windowsPhone`, `mac`, `winCE`, `winEmbedded`, `iPhone`, `iPad`, `iPod`, `android`, `iSocConsumer`, `unix`, `macMDM`, `holoLens`, `surfaceHub`, `androidForWork`, `androidEnterprise`, `blackberry`, `palm`, `unknown`. |
| osVersion | String | Operating system version of the device |
| tpmSpecificationVersion | String | Device TPM Version |
| deviceName | String | Device name |
| encryptionReadinessState | [encryptionReadinessState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-encryptionreadinessstate?view=graph-rest-beta) | Encryption readiness state. Possible values are: `notReady`, `ready`. |
| encryptionState | [encryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-encryptionstate?view=graph-rest-beta) | Device encryption state. Possible values are: `notEncrypted`, `encrypted`. |
| encryptionPolicySettingState | [complianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-compliancestatus?view=graph-rest-beta) | Encryption policy setting state. Possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`. |
| advancedBitLockerStates | [advancedBitLockerState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedbitlockerstate?view=graph-rest-beta) | Advanced BitLocker State. Possible values are: `success`, `noUserConsent`, `osVolumeUnprotected`, `osVolumeTpmRequired`, `osVolumeTpmOnlyRequired`, `osVolumeTpmPinRequired`, `osVolumeTpmStartupKeyRequired`, `osVolumeTpmPinStartupKeyRequired`, `osVolumeEncryptionMethodMismatch`, `recoveryKeyBackupFailed`, `fixedDriveNotEncrypted`, `fixedDriveEncryptionMethodMismatch`, `loggedOnUserNonAdmin`, `windowsRecoveryEnvironmentNotConfigured`, `tpmNotAvailable`, `tpmNotReady`, `networkError`. |
| fileVaultStates | [fileVaultState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-filevaultstate?view=graph-rest-beta) | FileVault State. Possible values are: `success`, `driveEncryptedByUser`, `userDeferredEncryption`, `escrowNotEnabled`. |
| policyDetails | [encryptionReportPolicyDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-encryptionreportpolicydetails?view=graph-rest-beta) collection | Policy Details |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDeviceEncryptionState",
  "id": "String (identifier)",
  "userPrincipalName": "String",
  "deviceType": "String",
  "osVersion": "String",
  "tpmSpecificationVersion": "String",
  "deviceName": "String",
  "encryptionReadinessState": "String",
  "encryptionState": "String",
  "encryptionPolicySettingState": "String",
  "advancedBitLockerStates": "String",
  "fileVaultStates": "String",
  "policyDetails": [
    {
      "@odata.type": "microsoft.graph.encryptionReportPolicyDetails",
      "policyId": "String",
      "policyName": "String"
    }
  ]
}
```
