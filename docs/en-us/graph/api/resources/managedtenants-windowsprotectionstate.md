<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-windowsprotectionstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# windowsProtectionState resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represent the Windows protection state for managed devices running Windows.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List Windows protection state](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-windowsprotectionstates?view=graph-rest-beta) | [microsoft.graph.managedTenants.windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-windowsprotectionstate?view=graph-rest-beta) collection | Get a list of the [windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-windowsprotectionstate?view=graph-rest-beta) objects and their properties. |
| [Get Windows protection state](https://learn.microsoft.com/en-us/graph/api/managedtenants-windowsprotectionstate-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-windowsprotectionstate?view=graph-rest-beta) | Read the properties and relationships of a [windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-windowsprotectionstate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| antiMalwareVersion | String | The anti-malware version for the managed device. Optional. Read-only. |
| attentionRequired | Boolean | A flag indicating whether attention is required for the managed device. Optional. Read-only. |
| deviceDeleted | Boolean | A flag indicating whether the managed device has been deleted. Optional. Read-only. |
| devicePropertyRefreshDateTime | DateTimeOffset | The date and time the device property has been refreshed. Optional. Read-only. |
| engineVersion | String | The anti-virus engine version for the managed device. Optional. Read-only. |
| fullScanOverdue | Boolean | A flag indicating whether quick scan is overdue for the managed device. Optional. Read-only. |
| fullScanRequired | Boolean | A flag indicating whether full scan is overdue for the managed device. Optional. Read-only. |
| id | String | The unique identifier for the Windows protection state. Required. Read-only. |
| lastFullScanDateTime | DateTimeOffset | The date and time a full scan was completed. Optional. Read-only. |
| lastFullScanSignatureVersion | String | The version anti-malware version used to perform the last full scan. Optional. Read-only. |
| lastQuickScanDateTime | DateTimeOffset | The date and time a quick scan was completed. Optional. Read-only. |
| lastQuickScanSignatureVersion | String | The version anti-malware version used to perform the last full scan. Optional. Read-only. |
| lastRefreshedDateTime | DateTimeOffset | Date and time the entity was last updated in the multi-tenant management platform. Optional. Read-only. |
| lastReportedDateTime | DateTimeOffset | The date and time the protection state was last reported for the managed device. Optional. Read-only. |
| malwareProtectionEnabled | Boolean | A flag indicating whether malware protection is enabled for the managed device. Optional. Read-only. |
| managedDeviceHealthState | String | The health state for the managed device. Optional. Read-only. |
| managedDeviceId | String | The unique identifier for the managed device. Optional. Read-only. |
| managedDeviceName | String | The display name for the managed device. Optional. Read-only. |
| networkInspectionSystemEnabled | Boolean | A flag indicating whether the network inspection system is enabled. Optional. Read-only. |
| quickScanOverdue | Boolean | A flag indicating weather a quick scan is overdue. Optional. Read-only. |
| realTimeProtectionEnabled | Boolean | A flag indicating whether real time protection is enabled. Optional. Read-only. |
| rebootRequired | Boolean | A flag indicating whether a reboot is required. Optional. Read-only. |
| signatureUpdateOverdue | Boolean | A flag indicating whether an signature update is overdue. Optional. Read-only. |
| signatureVersion | String | The signature version for the managed device. Optional. Read-only. |
| tenantDisplayName | String | The display name for the managed tenant. Optional. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.windowsProtectionState",
  "id": "String (identifier)",
  "tenantId": "String",
  "tenantDisplayName": "String",
  "managedDeviceId": "String",
  "managedDeviceName": "String",
  "malwareProtectionEnabled": "Boolean",
  "managedDeviceHealthState": "String",
  "realTimeProtectionEnabled": "Boolean",
  "networkInspectionSystemEnabled": "Boolean",
  "quickScanOverdue": "Boolean",
  "fullScanOverdue": "Boolean",
  "signatureUpdateOverdue": "Boolean",
  "rebootRequired": "Boolean",
  "attentionRequired": "Boolean",
  "fullScanRequired": "Boolean",
  "engineVersion": "String",
  "signatureVersion": "String",
  "antiMalwareVersion": "String",
  "lastQuickScanDateTime": "String (timestamp)",
  "lastFullScanDateTime": "String (timestamp)",
  "lastQuickScanSignatureVersion": "String",
  "lastFullScanSignatureVersion": "String",
  "lastReportedDateTime": "String (timestamp)",
  "devicePropertyRefreshDateTime": "String (timestamp)",
  "deviceDeleted": "Boolean",
  "lastRefreshedDateTime": "String (timestamp)"
}
```
