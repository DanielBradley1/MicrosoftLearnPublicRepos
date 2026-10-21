<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# customFieldValue resource type \(planner\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The value of a [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) set on a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta). `customFieldDefinitionId` references the owning plan's custom field definition.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/task-list-customfieldvalues?view=graph-rest-beta) | [customFieldValue](https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta) collection | Get a list of the customFieldValue objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/task-post-customfieldvalues?view=graph-rest-beta) | [customFieldValue](https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta) | Create a new customFieldValue object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/customfieldvalue-get?view=graph-rest-beta) | [customFieldValue](https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta) | Read the properties and relationships of [customFieldValue](https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/customfieldvalue-update?view=graph-rest-beta) | [customFieldValue](https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta) | Update the properties of a customFieldValue object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customFieldDefinitionId | String | ID of the customFieldDefinition this value is for. Immutable after creation. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| value | String | The value of the custom field, formatted according to the field's valueType. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customFieldValue",
  "id": "String (identifier)",
  "customFieldDefinitionId": "String",
  "value": "String"
}
```
