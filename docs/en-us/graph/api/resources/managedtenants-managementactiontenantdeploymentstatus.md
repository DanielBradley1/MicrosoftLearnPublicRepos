<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiontenantdeploymentstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# managementActionTenantDeploymentStatus resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents tenant level deployment status for the management action.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List management action deployment statuses](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-managementactiontenantdeploymentstatuses?view=graph-rest-beta) | [microsoft.graph.managedTenants.managementActionTenantDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiontenantdeploymentstatus?view=graph-rest-beta) collection | Get a list of the [managementActionTenantDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiontenantdeploymentstatus?view=graph-rest-beta) objects and their properties. |
| [Get management action deployment status](https://learn.microsoft.com/en-us/graph/api/managedtenants-managementactiontenantdeploymentstatus-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.managementActionTenantDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiontenantdeploymentstatus?view=graph-rest-beta) | Read the properties and relationships of a [managementActionTenantDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiontenantdeploymentstatus?view=graph-rest-beta) object. |
| [Change management action deployment status](https://learn.microsoft.com/en-us/graph/api/managedtenants-managementactiontenantdeploymentstatus-changedeploymentstatus?view=graph-rest-beta) | [microsoft.graph.managedTenants.managementActionDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiondeploymentstatus?view=graph-rest-beta) | Changes the deployment status for the management action. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the tenant level deployment status. Required. Read-only. |
| statuses | [microsoft.graph.managedTenants.managementActionDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiondeploymentstatus?view=graph-rest-beta) collection | The collection of deployment status for each instance of a management action. Optional. |
| tenantGroupId | String | The identifier for the tenant group that is associated with the management action. Required. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managementActionTenantDeploymentStatus",
  "id": "String (identifier)",
  "tenantGroupId": "String",
  "tenantId": "String",
  "statuses": [
    {
      "@odata.type": "microsoft.graph.managedTenants.managementActionDeploymentStatus"
    }
  ]
}
```
