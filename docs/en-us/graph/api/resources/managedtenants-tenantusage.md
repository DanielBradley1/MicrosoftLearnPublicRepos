<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantusage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# tenantUsage resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the number of monthly active users per service in a managed tenant for the previous month. The time period for the data is a sliding window that takes a snapshot once a day.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-tenantusage?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantUsage](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantusage?view=graph-rest-beta) collection | Gets the [monthly usage data for each service](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantusage?view=graph-rest-beta) in a [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managedtenant?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the tenant. Required. Read-only. |
| reportDateTime | DateTimeOffset | The day the report was generated for the previous month. Required. Read-only. |
| serviceUsages | [microsoft.graph.managedTenants.serviceUsage](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-serviceusage?view=graph-rest-beta) collection | The number of monthly active users for each service in the tenant. Example services: `Excel`, `Exchange`, `Intune`, `Outlook`, `Teams`, `Word`. Required. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Read-only. |
| totalActiveUsers | Int32 | The total number of unique, active users. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.tenantUsage",
  "id": "String (identifier)",
  "serviceUsages": [
    {
      "@odata.type": "microsoft.graph.managedTenants.serviceUsage"
    }
  ],
  "tenantId": "String",
  "reportDateTime": "String (timestamp)",
  "totalActiveUsers": "Integer"
}
```
