<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcdevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# cloudPcDevice resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a cloud PC device that belongs to a given managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List cloud PC devices](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-cloudpcdevices?view=graph-rest-beta) | [microsoft.graph.managedTenants.cloudPcDevice](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcdevice?view=graph-rest-beta) collection | Get a list of the [cloudPcDevice](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcdevice?view=graph-rest-beta) objects and their properties. |
| [Get cloud PC device](https://learn.microsoft.com/en-us/graph/api/managedtenants-cloudpcdevice-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.cloudPcDevice](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcdevice?view=graph-rest-beta) | Read the properties and relationships of a [cloudPcDevice](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcdevice?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudPcStatus | String | The status of the cloud PC. The possible values are: `notProvisioned`, `provisioning`, `provisioned`, `upgrading`, `inGracePeriod`, `deprovisioning`, `failed`. Required. Read-only. |
| deviceSpecification | String | The specification of the cloud PC device. Required. Read-only. |
| displayName | String | The display name of the cloud PC device. Required. Read-only. |
| id | String | The unique identifier of the cloud PC device. Required. Read-only. |
| lastRefreshedDateTime | DateTimeOffset | Date and time the entity was last updated in the multi-tenant management platform. Required. Read-only. |
| managedDeviceId | String | The managed device identifier of the cloud PC device. Optional. Read-only. |
| managedDeviceName | String | The managed device display name of the cloud PC device. Optional. Read-only. |
| provisioningPolicyId | String | The provisioning policy identifier for the cloud PC device. Required. Read-only. |
| servicePlanName | String | The service plan name of the cloud PC device. Required. Read-only. |
| servicePlanType | String | The service plan type of the cloud PC device. Required. Read-only. |
| tenantDisplayName | String | The display name for the managed tenant. Required. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Required. Read-only. |
| userPrincipalName | String | The user principal name \(UPN\) of the user assigned to the cloud PC device. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.cloudPcDevice",
  "cloudPcStatus": "String",
  "deviceSpecification": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastRefreshedDateTime": "String (timestamp)",
  "managedDeviceId": "String",
  "managedDeviceName": "String",
  "provisioningPolicyId": "String",
  "servicePlanName": "String",
  "servicePlanType": "String",
  "tenantDisplayName": "String",
  "tenantId": "String",
  "userPrincipalName": "String"
}     
```
