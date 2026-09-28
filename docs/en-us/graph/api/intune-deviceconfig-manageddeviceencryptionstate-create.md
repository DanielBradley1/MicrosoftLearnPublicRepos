<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-manageddeviceencryptionstate-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Create managedDeviceEncryptionState

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta) object.

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
POST /deviceManagement/managedDeviceEncryptionStates
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the managedDeviceEncryptionState object.

The following table shows the properties that are required when you create the managedDeviceEncryptionState.

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

## Response

If successful, this method returns a `201 Created` response code and a [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/managedDeviceEncryptionStates
Content-type: application/json
Content-length: 704

{
  "@odata.type": "#microsoft.graph.managedDeviceEncryptionState",
  "userPrincipalName": "User Principal Name value",
  "deviceType": "windowsRT",
  "osVersion": "Os Version value",
  "tpmSpecificationVersion": "Tpm Specification Version value",
  "deviceName": "Device Name value",
  "encryptionReadinessState": "ready",
  "encryptionState": "encrypted",
  "encryptionPolicySettingState": "notApplicable",
  "advancedBitLockerStates": "noUserConsent",
  "fileVaultStates": "driveEncryptedByUser",
  "policyDetails": [
    {
      "@odata.type": "microsoft.graph.encryptionReportPolicyDetails",
      "policyId": "Policy Id value",
      "policyName": "Policy Name value"
    }
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 753

{
  "@odata.type": "#microsoft.graph.managedDeviceEncryptionState",
  "id": "f09b4ab6-4ab6-f09b-b64a-9bf0b64a9bf0",
  "userPrincipalName": "User Principal Name value",
  "deviceType": "windowsRT",
  "osVersion": "Os Version value",
  "tpmSpecificationVersion": "Tpm Specification Version value",
  "deviceName": "Device Name value",
  "encryptionReadinessState": "ready",
  "encryptionState": "encrypted",
  "encryptionPolicySettingState": "notApplicable",
  "advancedBitLockerStates": "noUserConsent",
  "fileVaultStates": "driveEncryptedByUser",
  "policyDetails": [
    {
      "@odata.type": "microsoft.graph.encryptionReportPolicyDetails",
      "policyId": "Policy Id value",
      "policyName": "Policy Name value"
    }
  ]
}
```
