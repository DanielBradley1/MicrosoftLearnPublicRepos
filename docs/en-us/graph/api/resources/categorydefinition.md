<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/categorydefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# categoryDefinition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A named category that can be applied to [tasks](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) in a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta). It has no defaults beyond the universal property set.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/planview-list-categories?view=graph-rest-beta) | [categoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/categorydefinition?view=graph-rest-beta) collection | Get a list of the categoryDefinition objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/planview-post-categories?view=graph-rest-beta) | [categoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/categorydefinition?view=graph-rest-beta) | Create a new categoryDefinition object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/categorydefinition-get?view=graph-rest-beta) | [categoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/categorydefinition?view=graph-rest-beta) | Read the properties and relationships of [categoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/categorydefinition?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/categorydefinition-update?view=graph-rest-beta) | [categoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/categorydefinition?view=graph-rest-beta) | Update the properties of a categoryDefinition object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/planview-delete-categories?view=graph-rest-beta) | None | Delete a categoryDefinition object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capabilities | [categoryDefinitionCapability](https://learn.microsoft.com/en-us/graph/api/resources/categorydefinitioncapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| displayName | String | Name of the category. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.categoryDefinition",
  "id": "String (identifier)",
  "displayName": "String",
  "capabilities": {
    "@odata.type": "microsoft.graph.categoryDefinitionCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
