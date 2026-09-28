<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcconnection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# cloudPcConnection resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Cloud PC connection for a given managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List Cloud PC connections](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-cloudpcconnections?view=graph-rest-beta) | [microsoft.graph.managedTenants.cloudPcConnection](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcconnection?view=graph-rest-beta) collection | Get a list of the [cloudPcConnection](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcconnection?view=graph-rest-beta) objects and their properties. |
| [Get Cloud PC connection](https://learn.microsoft.com/en-us/graph/api/managedtenants-cloudpcconnection-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.cloudPcConnection](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcconnection?view=graph-rest-beta) | Read the properties and relationships of a [cloudPcConnection](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcconnection?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the cloud PC connection. Required. Read-only. |
| healthCheckStatus | String | The health status of the cloud PC connection. The possible values are: `pending`, `running`, `passed`, `failed`, `unknownFutureValue`. Required. Read-only. |
| id | String | The unique identifier for the cloud PC connection. Required. Read-only. |
| lastRefreshedDateTime | DateTimeOffset | Date and time the entity was last updated in the multi-tenant management platform. Required. Read-only. |
| tenantDisplayName | String | The display name for the managed tenant. Required. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.cloudPcConnection",
  "id": "String (identifier)",
  "displayName": "String",
  "tenantId": "String",
  "tenantDisplayName": "String",
  "healthCheckStatus": "String",
  "lastRefreshedDateTime": "String (timestamp)"
}
```
