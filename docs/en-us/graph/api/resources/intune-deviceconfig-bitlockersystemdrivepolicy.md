<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-bitlockersystemdrivepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# bitLockerSystemDrivePolicy resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

BitLocker Encryption Base Policies.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| encryptionMethod | [bitLockerEncryptionMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-bitlockerencryptionmethod?view=graph-rest-beta) | Select the encryption method for operating system drives. Possible values are: `aesCbc128`, `aesCbc256`, `xtsAes128`, `xtsAes256`. |
| startupAuthenticationRequired | Boolean | Require additional authentication at startup. |
| startupAuthenticationBlockWithoutTpmChip | Boolean | Indicates whether to allow BitLocker without a compatible TPM \(requires a password or a startup key on a USB flash drive\). |
| startupAuthenticationTpmUsage | [configurationUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-configurationusage?view=graph-rest-beta) | Indicates if TPM startup is allowed/required/disallowed. Possible values are: `blocked`, `required`, `allowed`, `notConfigured`. |
| startupAuthenticationTpmPinUsage | [configurationUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-configurationusage?view=graph-rest-beta) | Indicates if TPM startup pin is allowed/required/disallowed. Possible values are: `blocked`, `required`, `allowed`, `notConfigured`. |
| startupAuthenticationTpmKeyUsage | [configurationUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-configurationusage?view=graph-rest-beta) | Indicates if TPM startup key is allowed/required/disallowed. Possible values are: `blocked`, `required`, `allowed`, `notConfigured`. |
| startupAuthenticationTpmPinAndKeyUsage | [configurationUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-configurationusage?view=graph-rest-beta) | Indicates if TPM startup pin key and key are allowed/required/disallowed. Possible values are: `blocked`, `required`, `allowed`, `notConfigured`. |
| minimumPinLength | Int32 | Indicates the minimum length of startup pin. Valid values 4 to 20 |
| recoveryOptions | [bitLockerRecoveryOptions](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-bitlockerrecoveryoptions?view=graph-rest-beta) | Allows to recover BitLocker encrypted operating system drives in the absence of the required startup key information. This policy setting is applied when you turn on BitLocker. |
| prebootRecoveryEnableMessageAndUrl | Boolean | Enable pre-boot recovery message and Url. If requireStartupAuthentication is false, this value does not affect. |
| prebootRecoveryMessage | String | Defines a custom recovery message. |
| prebootRecoveryUrl | String | Defines a custom recovery URL. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.bitLockerSystemDrivePolicy",
  "encryptionMethod": "String",
  "startupAuthenticationRequired": true,
  "startupAuthenticationBlockWithoutTpmChip": true,
  "startupAuthenticationTpmUsage": "String",
  "startupAuthenticationTpmPinUsage": "String",
  "startupAuthenticationTpmKeyUsage": "String",
  "startupAuthenticationTpmPinAndKeyUsage": "String",
  "minimumPinLength": 1024,
  "recoveryOptions": {
    "@odata.type": "microsoft.graph.bitLockerRecoveryOptions",
    "blockDataRecoveryAgent": true,
    "recoveryPasswordUsage": "String",
    "recoveryKeyUsage": "String",
    "hideRecoveryOptions": true,
    "enableRecoveryInformationSaveToStore": true,
    "recoveryInformationToStore": "String",
    "enableBitLockerAfterRecoveryInformationToStore": true
  },
  "prebootRecoveryEnableMessageAndUrl": true,
  "prebootRecoveryMessage": "String",
  "prebootRecoveryUrl": "String"
}
```
