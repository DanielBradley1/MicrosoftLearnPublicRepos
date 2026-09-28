<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# tenant resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a tenant associated with the managing entity.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List tenants](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-tenants?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta) collection | Get a list of the [tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta) objects and their properties. |
| [Get tenant](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenant-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta) | Read the properties and relationships of a [tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta) object. |
| [Offboard tenant](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenant-offboardtenant?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta) | Off boards a tenant from the multi-tenant management platform. |
| [Reset tenant onboarding status](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenant-resettenantonboardingstatus?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta) | Resets the tenant onboarding status with the multi-tenant management platform. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contract | [microsoft.graph.managedTenants.tenantContract](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcontract?view=graph-rest-beta) | The relationship details for the tenant with the managing entity. |
| createdDateTime | DateTimeOffset | The date and time the tenant was created in the multi-tenant management platform. Optional. Read-only. |
| displayName | String | The display name for the tenant. Required. Read-only. |
| id | String | The Microsoft Entra tenant identifier for the tenant. Required. Read-only. |
| lastUpdatedDateTime | DateTimeOffset | The date and time the tenant was last updated within the multi-tenant management platform. Optional. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Optional. Read-only. |
| tenantStatusInformation | [microsoft.graph.managedTenants.tenantStatusInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantstatusinformation?view=graph-rest-beta) | The onboarding status information for the tenant. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.tenant",
  "contract": {"@odata.type": "microsoft.graph.managedTenants.tenantContract"},
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "lastUpdatedDateTime": "String (timestamp)",
  "tenantId": "String",
  "tenantStatusInformation": {"@odata.type": "microsoft.graph.managedTenants.tenantStatusInformation"}
}
```
