<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managedtenantoperationerror?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# managedTenantOperationError resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents an error for a managed tenant operation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | String | The error message for the exception. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managedTenantOperationError",
  "tenantId": "String",
  "error": "String"
}
```
