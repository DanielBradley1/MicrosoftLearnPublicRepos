<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationerror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# synchronizationError resource type

Namespace: microsoft.graph

Represents an error that occurred during the synchronization process. Configured in the **error** property of the [synchronizationTaskExecution](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtaskexecution?view=graph-rest-1.0) and [synchronizationQuarantine](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationquarantine?view=graph-rest-1.0) resources.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The error code. For example, `AzureDirectoryB2BManagementPolicyCheckFailure`. |
| message | String | The error message. For example, `Policy permitting auto-redemption of invitations not configured`. |
| tenantActionable | Boolean | The action to take to resolve the error. For example, `false`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "code": "String",
  "message": "String",
  "tenantActionable": "Boolean"
}
```
