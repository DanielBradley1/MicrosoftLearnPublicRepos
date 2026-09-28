<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementintent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# managementIntent resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents metadata for a baseline and what management templates are included.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List management intents](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-managementintents?view=graph-rest-beta) | [microsoft.graph.managedTenants.managementIntent](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementintent?view=graph-rest-beta) collection | Get a list of the [managementIntent](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementintent?view=graph-rest-beta) objects and their properties. |
| [Get management intent](https://learn.microsoft.com/en-us/graph/api/managedtenants-managementintent-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.managementIntent](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementintent?view=graph-rest-beta) | Read the properties and relationships of a [managementIntent](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementintent?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name for the management intent. Optional. Read-only. |
| id | String | The unique identifier for the management intent. Required. Read-only. |
| isGlobal | Boolean | A flag indicating whether the management intent is global. Required. Read-only. |
| managementTemplates | [microsoft.graph.managedTenants.managementTemplateDetailedInfo](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementtemplatedetailedinfo?view=graph-rest-beta) collection | The collection of management templates associated with the management intent. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managementIntent",
  "id": "String (identifier)",
  "displayName": "String",
  "isGlobal": "Boolean",
  "managementTemplates": [
    {
      "@odata.type": "microsoft.graph.managedTenants.managementTemplateDetailedInfo"
    }
  ]
}
```
