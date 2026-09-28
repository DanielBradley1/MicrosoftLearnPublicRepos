<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-bitlockerrecoveryoptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# bitLockerRecoveryOptions resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

BitLocker Recovery Options.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blockDataRecoveryAgent | Boolean | Indicates whether to block certificate-based data recovery agent. |
| recoveryPasswordUsage | [configurationUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-configurationusage?view=graph-rest-beta) | Indicates whether users are allowed or required to generate a 48-digit recovery password for fixed or system disk. Possible values are: `blocked`, `required`, `allowed`, `notConfigured`. |
| recoveryKeyUsage | [configurationUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-configurationusage?view=graph-rest-beta) | Indicates whether users are allowed or required to generate a 256-bit recovery key for fixed or system disk. Possible values are: `blocked`, `required`, `allowed`, `notConfigured`. |
| hideRecoveryOptions | Boolean | Indicates whether or not to allow showing recovery options in BitLocker Setup Wizard for fixed or system disk. |
| enableRecoveryInformationSaveToStore | Boolean | Indicates whether or not to allow BitLocker recovery information to store in AD DS. |
| recoveryInformationToStore | [bitLockerRecoveryInformationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-bitlockerrecoveryinformationtype?view=graph-rest-beta) | Configure what pieces of BitLocker recovery information are stored to AD DS. Possible values are: `passwordAndKey`, `passwordOnly`. |
| enableBitLockerAfterRecoveryInformationToStore | Boolean | Indicates whether or not to enable BitLocker until recovery information is stored in AD DS. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.bitLockerRecoveryOptions",
  "blockDataRecoveryAgent": true,
  "recoveryPasswordUsage": "String",
  "recoveryKeyUsage": "String",
  "hideRecoveryOptions": true,
  "enableRecoveryInformationSaveToStore": true,
  "recoveryInformationToStore": "String",
  "enableBitLockerAfterRecoveryInformationToStore": true
}
```
