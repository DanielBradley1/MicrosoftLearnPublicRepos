<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-devicecompliancepolicysettingstatesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# deviceCompliancePolicySettingStateSummary resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a summary of device compliance policy setting states for a given managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List device compliance policy setting state summary](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-devicecompliancepolicysettingstatesummary?view=graph-rest-beta) | [microsoft.graph.managedTenants.deviceCompliancePolicySettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-devicecompliancepolicysettingstatesummary?view=graph-rest-beta) collection | Get a list of the [deviceCompliancePolicySettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-devicecompliancepolicysettingstatesummary?view=graph-rest-beta) objects and their properties. |
| [Get device compliance policy setting state summary](https://learn.microsoft.com/en-us/graph/api/managedtenants-devicecompliancepolicysettingstatesummary-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.deviceCompliancePolicySettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-devicecompliancepolicysettingstatesummary?view=graph-rest-beta) | Read the properties and relationships of a [deviceCompliancePolicySettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-devicecompliancepolicysettingstatesummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for this entity. Required. Read-only. |
| conflictDeviceCount | Int32 | The number of devices in a conflict state. Optional. Read-only. |
| errorDeviceCount | Int32 | The number of devices in an error state. Optional. Read-only. |
| failedDeviceCount | Int32 | The number of devices in a failed state. Optional. Read-only. |
| intuneAccountId | String | The identifer for the Microsoft Intune account. Required. Read-only. |
| intuneSettingId | String | The identifier for the Intune setting. Optional. Read-only. |
| lastRefreshedDateTime | DateTimeOffset | Date and time the entity was last updated in the multi-tenant management platform. Optional. Read-only. |
| notApplicableDeviceCount | Int32 | The number of devices in a not applicable state. Optional. Read-only. |
| pendingDeviceCount | Int32 | The number of devices in a pending state. Optional. Read-only. |
| policyType | String | The type for the device compliance policy. Optional. Read-only. |
| settingName | String | The name for the setting within the device compliance policy. Optional. Read-only. |
| succeededDeviceCount | Int32 | The number of devices in a succeeded state. Optional. Read-only. |
| tenantDisplayName | String | The display name for the managed tenant. Required. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.deviceCompliancePolicySettingStateSummary",
  "id": "String (identifier)",
  "tenantId": "String",
  "tenantDisplayName": "String",
  "conflictDeviceCount": "Integer",
  "errorDeviceCount": "Integer",
  "failedDeviceCount": "Integer",
  "intuneAccountId": "String",
  "intuneSettingId": "String",
  "notApplicableDeviceCount": "Integer",
  "pendingDeviceCount": "Integer",
  "policyType": "String",
  "settingName": "String",
  "succeededDeviceCount": "Integer",
  "lastRefreshedDateTime": "String (timestamp)"
}
```
