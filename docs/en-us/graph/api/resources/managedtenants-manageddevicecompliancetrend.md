<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliancetrend?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# managedDeviceComplianceTrend resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a trend of compliant and non-compliant devices for a given managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List managed device compliance trend](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-manageddevicecompliancetrends?view=graph-rest-beta) | [microsoft.graph.managedTenants.managedDeviceComplianceTrend](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliancetrend?view=graph-rest-beta) collection | Get a list of the [managedDeviceComplianceTrend](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliancetrend?view=graph-rest-beta) objects and their properties. |
| [Get managed device compliance trend](https://learn.microsoft.com/en-us/graph/api/managedtenants-manageddevicecompliancetrend-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.managedDeviceComplianceTrend](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliancetrend?view=graph-rest-beta) | Read the properties and relationships of a [managedDeviceComplianceTrend](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliancetrend?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| compliantDeviceCount | Int32 | The number of devices with a compliant status. Required. Read-only. |
| configManagerDeviceCount | Int32 | The number of devices manged by Configuration Manager. Required. Read-only. |
| countDateTime | String | The date and time compliance snapshot was performed. Required. Read-only. |
| errorDeviceCount | Int32 | The number of devices with an error status. Required. Read-only. |
| id | String | The unique identifier for this entity. Required. Read-only. |
| inGracePeriodDeviceCount | Int32 | The number of devices that are in a grace period status. Required. Read-only. |
| noncompliantDeviceCount | Int32 | The number of devices that are in a non-compliant status. Required. Read-only. |
| tenantDisplayName | String | The display name for the managed tenant. Optional. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Optional. Read-only. |
| unknownDeviceCount | Int32 | The number of devices in an unknown status. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managedDeviceComplianceTrend",
  "id": "String (identifier)",
  "tenantId": "String",
  "tenantDisplayName": "String",
  "unknownDeviceCount": "Integer",
  "compliantDeviceCount": "Integer",
  "noncompliantDeviceCount": "Integer",
  "errorDeviceCount": "Integer",
  "inGracePeriodDeviceCount": "Integer",
  "configManagerDeviceCount": "Integer",
  "countDateTime": "String"
}
```
