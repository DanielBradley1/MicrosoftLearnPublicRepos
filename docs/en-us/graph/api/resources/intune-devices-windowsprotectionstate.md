<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsprotectionstate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# windowsProtectionState resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device protection status entity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsprotectionstate-get?view=graph-rest-1.0) | [windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsprotectionstate?view=graph-rest-1.0) | Read properties and relationships of the [windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsprotectionstate?view=graph-rest-1.0) object. |
| [Update windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsprotectionstate-update?view=graph-rest-1.0) | [windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsprotectionstate?view=graph-rest-1.0) | Update the properties of a [windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsprotectionstate?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique Identifier for the device protection status object. This is device id of the device |
| malwareProtectionEnabled | Boolean | When TRUE indicates anti malware is enabled when FALSE indicates anti malware is not enabled. |
| deviceState | [windowsDeviceHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsdevicehealthstate?view=graph-rest-1.0) | Indicates device's health state. The possible values are: clean, fullScanPending, rebootPending, manualStepsPending, offlineScanPending, critical. The possible values are: `clean`, `fullScanPending`, `rebootPending`, `manualStepsPending`, `offlineScanPending`, `critical`. |
| realTimeProtectionEnabled | Boolean | When TRUE indicates real time protection is enabled, when FALSE indicates real time protection is not enabled. Defaults to setting on client device. |
| networkInspectionSystemEnabled | Boolean | When TRUE indicates network inspection system enabled, when FALSE indicates network inspection system is not enabled. Defaults to setting on client device. |
| quickScanOverdue | Boolean | When TRUE indicates quick scan is overdue, when FALSE indicates quick scan is not overdue. Defaults to setting on client device. |
| fullScanOverdue | Boolean | When TRUE indicates full scan is overdue, when FALSE indicates full scan is not overdue. Defaults to setting on client device. |
| signatureUpdateOverdue | Boolean | When TRUE indicates signature is out of date, when FALSE indicates signature is not out of date. Defaults to setting on client device. |
| rebootRequired | Boolean | When TRUE indicates reboot is required, when FALSE indicates when TRUE indicates reboot is not required. Defaults to setting on client device. |
| fullScanRequired | Boolean | When TRUE indicates full scan is required, when FALSE indicates full scan is not required. Defaults to setting on client device. |
| engineVersion | String | Current endpoint protection engine's version |
| signatureVersion | String | Current malware definitions version |
| antiMalwareVersion | String | Current anti malware version |
| lastQuickScanDateTime | DateTimeOffset | Last quick scan datetime |
| lastFullScanDateTime | DateTimeOffset | Last quick scan datetime |
| lastQuickScanSignatureVersion | String | Last quick scan signature version |
| lastFullScanSignatureVersion | String | Last full scan signature version |
| lastReportedDateTime | DateTimeOffset | Last device health status reported time |
| productStatus | [windowsDefenderProductStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsdefenderproductstatus?view=graph-rest-1.0) | Product Status of Windows Defender Antivirus. The possible values are: noStatus, serviceNotRunning, serviceStartedWithoutMalwareProtection, pendingFullScanDueToThreatAction, pendingRebootDueToThreatAction, pendingManualStepsDueToThreatAction, avSignaturesOutOfDate, asSignaturesOutOfDate, noQuickScanHappenedForSpecifiedPeriod, noFullScanHappenedForSpecifiedPeriod, systemInitiatedScanInProgress, systemInitiatedCleanInProgress, samplesPendingSubmission, productRunningInEvaluationMode, productRunningInNonGenuineMode, productExpired, offlineScanRequired, serviceShutdownAsPartOfSystemShutdown, threatRemediationFailedCritically, threatRemediationFailedNonCritically, noStatusFlagsSet, platformOutOfDate, platformUpdateInProgress, platformAboutToBeOutdated, signatureOrPlatformEndOfLifeIsPastOrIsImpending, windowsSModeSignaturesInUseOnNonWin10SInstall. The possible values are: `noStatus`, `serviceNotRunning`, `serviceStartedWithoutMalwareProtection`, `pendingFullScanDueToThreatAction`, `pendingRebootDueToThreatAction`, `pendingManualStepsDueToThreatAction`, `avSignaturesOutOfDate`, `asSignaturesOutOfDate`, `noQuickScanHappenedForSpecifiedPeriod`, `noFullScanHappenedForSpecifiedPeriod`, `systemInitiatedScanInProgress`, `systemInitiatedCleanInProgress`, `samplesPendingSubmission`, `productRunningInEvaluationMode`, `productRunningInNonGenuineMode`, `productExpired`, `offlineScanRequired`, `serviceShutdownAsPartOfSystemShutdown`, `threatRemediationFailedCritically`, `threatRemediationFailedNonCritically`, `noStatusFlagsSet`, `platformOutOfDate`, `platformUpdateInProgress`, `platformAboutToBeOutdated`, `signatureOrPlatformEndOfLifeIsPastOrIsImpending`, `windowsSModeSignaturesInUseOnNonWin10SInstall`. |
| isVirtualMachine | Boolean | When TRUE indicates the device is a virtual machine, when FALSE indicates the device is not a virtual machine. Defaults to setting on client device. |
| tamperProtectionEnabled | Boolean | When TRUE indicates the Windows Defender tamper protection feature is enabled, when FALSE indicates the Windows Defender tamper protection feature is not enabled. Defaults to setting on client device. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| detectedMalwareState | [windowsDeviceMalwareState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsdevicemalwarestate?view=graph-rest-1.0) collection | Device malware list |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsProtectionState",
  "id": "String (identifier)",
  "malwareProtectionEnabled": true,
  "deviceState": "String",
  "realTimeProtectionEnabled": true,
  "networkInspectionSystemEnabled": true,
  "quickScanOverdue": true,
  "fullScanOverdue": true,
  "signatureUpdateOverdue": true,
  "rebootRequired": true,
  "fullScanRequired": true,
  "engineVersion": "String",
  "signatureVersion": "String",
  "antiMalwareVersion": "String",
  "lastQuickScanDateTime": "String (timestamp)",
  "lastFullScanDateTime": "String (timestamp)",
  "lastQuickScanSignatureVersion": "String",
  "lastFullScanSignatureVersion": "String",
  "lastReportedDateTime": "String (timestamp)",
  "productStatus": "String",
  "isVirtualMachine": true,
  "tamperProtectionEnabled": true
}
```
