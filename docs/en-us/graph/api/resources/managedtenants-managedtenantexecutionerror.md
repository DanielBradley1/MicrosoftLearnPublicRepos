<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managedtenantexecutionerror?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# managedTenantExecutionError resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an exception for a managed tenant operation.

Inherits from [managedTenantOperationError](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managedtenantoperationerror?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | String | The error message for the exception. Inherited from [managedTenantOperationError](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managedtenantoperationerror?view=graph-rest-beta). Required. Read-only. |
| errorDetails | String | Additional error information for the exception. Optional. Read-only. |
| nodeId | Int32 | The node identifier where the exception occurred. Required. Read-only. |
| rawToken | String | The token for the exception. Optional. Read-only. |
| statementIndex | Int32 | The statement index for the exception. Required. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the managed tenant. Inherited from [managedTenantOperationError](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managedtenantoperationerror?view=graph-rest-beta). Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managedTenantExecutionError",
  "tenantId": "String",
  "error": "String",
  "rawToken": "String",
  "statementIndex": "Integer",
  "nodeId": "Integer",
  "errorDetails": "String"
}
```
