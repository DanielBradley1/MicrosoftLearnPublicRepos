<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcoverview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# cloudPcOverview resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an overview of cloud PCs for a given managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List cloud PC overviews](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-cloudpcsoverview?view=graph-rest-beta) | [microsoft.graph.managedTenants.cloudPcOverview](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcoverview?view=graph-rest-beta) collection | Get a list of the [cloudPcOverview](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcoverview?view=graph-rest-beta) objects and their properties. |
| [Get cloud PC overview](https://learn.microsoft.com/en-us/graph/api/managedtenants-cloudpcoverview-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.cloudPcOverview](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcoverview?view=graph-rest-beta) | Read the properties and relationships of a [cloudPcOverview](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcoverview?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| frontlineLicensesCount | Int32 | The total number of cloud PC devices that have the `Frontline` SKU. Optional. Read-only. |
| id | String | The unique identifier for the cloud PC overview. Required. Read-only. |
| lastRefreshedDateTime | DateTimeOffset | Date and time the entity was last updated in the multi-tenant management platform. Optional. Read-only. |
| numberOfCloudPcConnectionStatusFailed | Int32 | The number of cloud PC connections that have a status of `failed`. Optional. Read-only. |
| numberOfCloudPcConnectionStatusPassed | Int32 | The number of cloud PC connections that have a status of `passed`. Optional. Read-only. |
| numberOfCloudPcConnectionStatusPending | Int32 | The number of cloud PC connections that have a status of `pending`. Optional. Read-only. |
| numberOfCloudPcConnectionStatusRunning | Int32 | The number of cloud PC connections that have a status of `running`. Optional. Read-only. |
| numberOfCloudPcConnectionStatusUnkownFutureValue | Int32 | The number of cloud PC connections that have a status of `unknownFutureValue`. Optional. Read-only. |
| numberOfCloudPcStatusDeprovisioning | Int32 | The number of cloud PCs that have a status of `deprovisioning`. Optional. Read-only. |
| numberOfCloudPcStatusFailed | Int32 | The number of cloud PCs that have a status of `failed`. Optional. Read-only. |
| numberOfCloudPcStatusInGracePeriod | Int32 | The number of cloud PCs that have a status of `inGracePeriod`. Optional. Read-only. |
| numberOfCloudPcStatusNotProvisioned | Int32 | The number of cloud PCs that have a status of `notProvisioned`. Optional. Read-only. |
| numberOfCloudPcStatusProvisioned | Int32 | The number of cloud PCs that have a status of `provisioned`. Optional. Read-only. |
| numberOfCloudPcStatusProvisioning | Int32 | The number of cloud PCs that have a status of `provisioning`. Optional. Read-only. |
| numberOfCloudPcStatusUnknown | Int32 | The number of cloud PCs that have a status of `unknown`. Optional. Read-only. |
| numberOfCloudPcStatusUpgrading | Int32 | The number of cloud PCs that have a status of `upgrading`. Optional. Read-only. |
| tenantDisplayName | String | The display name for the managed tenant. Optional. Read-only. |
| totalBusinessLicenses | Int32 | The total number of cloud PC devices that have the `Business` SKU. Optional. Read-only. |
| totalCloudPcConnectionStatus | Int32 | The total number of cloud PC connection statuses for the given managed tenant. Optional. Read-only. |
| totalCloudPcStatus | Int32 | The total number of cloud PC statues for the given managed tenant. Optional. Read-only. |
| totalEnterpriseLicenses | Int32 | The total number of cloud PC devices that have the `Enterprise` SKU. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.cloudPcOverview",
  "frontlineLicensesCount": "Integer",
  "id": "String (identifier)",
  "lastRefreshedDateTime": "String (timestamp)",
  "numberOfCloudPcConnectionStatusFailed": "Integer",
  "numberOfCloudPcConnectionStatusPassed": "Integer",
  "numberOfCloudPcConnectionStatusPending": "Integer",
  "numberOfCloudPcConnectionStatusRunning": "Integer",
  "numberOfCloudPcConnectionStatusUnkownFutureValue": "Integer",
  "numberOfCloudPcStatusDeprovisioning": "Integer",
  "numberOfCloudPcStatusFailed": "Integer",
  "numberOfCloudPcStatusInGracePeriod": "Integer",
  "numberOfCloudPcStatusNotProvisioned": "Integer",
  "numberOfCloudPcStatusProvisioned": "Integer",
  "numberOfCloudPcStatusProvisioning": "Integer",
  "numberOfCloudPcStatusUnknown": "Integer",
  "numberOfCloudPcStatusUpgrading": "Integer",
  "tenantDisplayName": "String",
  "totalBusinessLicenses": "Integer",
  "totalCloudPcConnectionStatus": "Integer",
  "totalCloudPcStatus": "Integer",
  "totalEnterpriseLicenses": "Integer"
}
```
