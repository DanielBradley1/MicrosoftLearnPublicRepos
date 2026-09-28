<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# managementAction resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a baseline management action for a given managed tenant. Examples of management actions are device encryption, perform configurations to allow Microsoft Entra device enrollment, and require multi-factor authentication for admins.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List management action](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-managementactions?view=graph-rest-beta) | [microsoft.graph.managedTenants.managementAction](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementaction?view=graph-rest-beta) collection | Get a list of the [managementAction](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementaction?view=graph-rest-beta) objects and their properties. |
| [Get management action](https://learn.microsoft.com/en-us/graph/api/managedtenants-managementaction-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.managementAction](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementaction?view=graph-rest-beta) | Read the properties and relationships of a [managementAction](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementaction?view=graph-rest-beta) object. |
| [Apply management action](https://learn.microsoft.com/en-us/graph/api/managedtenants-managementaction-apply?view=graph-rest-beta) | [microsoft.graph.managedTenants.managementActionDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiondeploymentstatus?view=graph-rest-beta) | Applies the management actions against the managed tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | managementCategory | The category for the management action. The possible values are: `custom`, `devices`, `identity`, `unknownFutureValue`. Optional. Read-only. |
| description | String | The description for the management action. Optional. Read-only. |
| displayName | String | The display name for the management action. Optional. Read-only. |
| id | String | The unique identifier for the management action. Required. Read-only. |
| referenceTemplateId | String | The reference for the management template used to generate the management action. Required. Read-only. |
| workloadActions | [microsoft.graph.managedTenants.workloadAction](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-workloadaction?view=graph-rest-beta) collection | The collection of workload actions associated with the management action. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managementAction",
  "id": "String (identifier)",
  "referenceTemplateId": "String",
  "displayName": "String",
  "description": "String",
  "category": "String",
  "workloadActions": [
    {
      "@odata.type": "microsoft.graph.managedTenants.workloadAction"
    }
  ]
}
```
