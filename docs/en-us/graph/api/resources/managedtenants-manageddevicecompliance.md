<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# managedDeviceCompliance resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the state of device compliance for each managed device belonging to a given managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List managed device compliances](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-manageddevicecompliances?view=graph-rest-beta) | [microsoft.graph.managedTenants.managedDeviceCompliance](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliance?view=graph-rest-beta) collection | Get a list of the [managedDeviceCompliance](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliance?view=graph-rest-beta) objects and their properties. |
| [Get managed device compliance](https://learn.microsoft.com/en-us/graph/api/managedtenants-manageddevicecompliance-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.managedDeviceCompliance](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliance?view=graph-rest-beta) | Read the properties and relationships of a [managedDeviceCompliance](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliance?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| complianceStatus | String | Compliance state of the device. This property is read-only. The possible values are: `unknown`, `compliant`, `noncompliant`, `conflict`, `error`, `inGracePeriod`, `configManager`. Optional. Read-only. |
| deviceType | String | Platform of the device. This property is read-only. The possible values are: `desktop`, `windowsRT`, `winMO6`, `nokia`, `windowsPhone`, `mac`, `winCE`, `winEmbedded`, `iPhone`, `iPad`, `iPod`, `android`, `iSocConsumer`, `unix`, `macMDM`, `holoLens`, `surfaceHub`, `androidForWork`, `androidEnterprise`, `windows10x`, `androidnGMS`, `chromeOS`, `linux`, `blackberry`, `palm`, `unknown`, `cloudPC`. Optional. Read-only. |
| id | String | The unique identity for this entity. Required. Read-only. |
| inGracePeriodUntilDateTime | DateTimeOffset | The date and time when the grace period will expire. Optional. Read-only. |
| lastRefreshedDateTime | DateTimeOffset | Date and time the entity was last updated in the multi-tenant management platform. Optional. Read-only. |
| lastSyncDateTime | DateTimeOffset | The date and time that the device last completed a successful sync with Microsoft Endpoint Manager. Optional. Read-only. |
| managedDeviceId | String | The identifier for the managed device in Microsoft Endpoint Manager. Optional. Read-only. |
| managedDeviceName | String | The display name for the managed device. Optional. Read-only. |
| manufacturer | String | The manufacture for the device. Optional. Read-only. |
| model | String | The model for the device. Optional. Read-only. |
| osDescription | String | The description of the operating system for the managed device. Optional. Read-only. |
| osVersion | String | The version of the operating system for the managed device. Optional. Read-only. |
| ownerType | String | The type of owner for the managed device. Optional. Read-only. |
| tenantDisplayName | String | The display name for the managed tenant. Optional. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managedDeviceCompliance",
  "id": "String (identifier)",
  "tenantId": "String",
  "tenantDisplayName": "String",
  "managedDeviceId": "String",
  "managedDeviceName": "String",
  "complianceStatus": "String",
  "osDescription": "String",
  "osVersion": "String",
  "lastSyncDateTime": "String (timestamp)",
  "ownerType": "String",
  "model": "String",
  "manufacturer": "String",
  "inGracePeriodUntilDateTime": "String (timestamp)",
  "lastRefreshedDateTime": "String (timestamp)",
  "deviceType": "String"
}
```
