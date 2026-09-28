<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-serviceusage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# serviceUsage resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents monthly active usage data for a service in a managed tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| monthlyActiveUsers | Int32 | Number of monthly active users of the service. Required. Read-only. |
| serviceName | String | The name for the Microsoft 365 service that generated the usage. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.serviceUsage",
  "serviceName": "String",
  "monthlyActiveUsers": "Integer"
}
```
