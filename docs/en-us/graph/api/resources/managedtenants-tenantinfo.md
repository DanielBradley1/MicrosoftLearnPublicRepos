<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# tenantInfo resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information for a managed tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.tenantInfo",
  "tenantId": "String"
}
```
