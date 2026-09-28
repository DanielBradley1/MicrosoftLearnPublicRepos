<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantdetailedinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# tenantDetailedInformation resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information for a managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List tenant detailed information](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-tenantsdetailedinformation?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantDetailedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantdetailedinformation?view=graph-rest-beta) collection | Get a list of the [tenantDetailedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantdetailedinformation?view=graph-rest-beta) objects and their properties. |
| [Get tenant detailed information](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenantdetailedinformation-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantDetailedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantdetailedinformation?view=graph-rest-beta) | Read the properties and relationships of a [tenantDetailedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantdetailedinformation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| city | String | The city where the managed tenant is located. Optional. Read-only. |
| countryCode | String | The code for the country where the managed tenant is located. Optional. Read-only. |
| countryName | String | The name for the country where the managed tenant is located. Optional. Read-only. |
| defaultDomainName | String | The default domain name for the managed tenant. Optional. Read-only. |
| displayName | String | The display name for the managed tenant. |
| id | String | The unique identifier for this entity. Required. Read-only. |
| industryName | String | The business industry associated with the managed tenant. Optional. Read-only. |
| region | String | The region where the managed tenant is located. Optional. Read-only. |
| segmentName | String | The business segment associated with the managed tenant. Optional. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). |
| verticalName | String | The vertical associated with the managed tenant. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.tenantDetailedInformation",
  "id": "String (identifier)",
  "tenantId": "String",
  "displayName": "String",
  "defaultDomainName": "String",
  "countryName": "String",
  "countryCode": "String",
  "city": "String",
  "region": "String",
  "verticalName": "String",
  "industryName": "String",
  "segmentName": "String"
}
```
