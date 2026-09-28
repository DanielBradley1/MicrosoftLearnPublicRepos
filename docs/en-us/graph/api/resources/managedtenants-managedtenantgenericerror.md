<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managedtenantgenericerror?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# managedTenantGenericError resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a generic error for a managed tenant.

Inherits from [managedTenantOperationError](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managedtenantoperationerror?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | String | The error message for the exception. Inherited from [managedTenantOperationError](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managedtenantoperationerror?view=graph-rest-beta). Required. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the managed tenant. Inherited from [managedTenantOperationError](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managedtenantoperationerror?view=graph-rest-beta). Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managedTenantGenericError",
  "tenantId": "String",
  "error": "String"
}
```
