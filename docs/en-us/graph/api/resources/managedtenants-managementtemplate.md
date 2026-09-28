<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementtemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# managementTemplate resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a group of actions and setting that can be performed against a managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List management templates](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-managementtemplates?view=graph-rest-beta) | [microsoft.graph.managedTenants.managementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementtemplate?view=graph-rest-beta) collection | Get a list of the [managementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementtemplate?view=graph-rest-beta) objects and their properties. |
| [Get management template](https://learn.microsoft.com/en-us/graph/api/managedtenants-managementtemplate-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.managementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementtemplate?view=graph-rest-beta) | Read the properties and relationships of a [managementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementtemplate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | managementCategory | The management category for the management template. The possible values are: `custom`, `devices`, `identity`, `unknownFutureValue`. Required. Read-only. |
| description | String | The description for the management template. Optional. Read-only. |
| displayName | String | The display name for the management template. Required. Read-only. |
| id | String | The unique identifier for the management template. Required. Read-only. |
| parameters | [microsoft.graph.managedTenants.templateParameter](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-templateparameter?view=graph-rest-beta) collection | The collection of parameters used by the management template. Optional. Read-only. |
| workloadActions | [microsoft.graph.managedTenants.workloadAction](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-workloadaction?view=graph-rest-beta) collection | The collection of workload actions associated with the management template. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managementTemplate",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "category": "String",
  "parameters": [
    {
      "@odata.type": "microsoft.graph.managedTenants.templateParameter"
    }
  ],
  "workloadActions": [
    {
      "@odata.type": "microsoft.graph.managedTenants.workloadAction"
    }
  ]
}
```
