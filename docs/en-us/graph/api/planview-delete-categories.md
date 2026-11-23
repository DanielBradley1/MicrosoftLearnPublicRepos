<!-- Source: https://learn.microsoft.com/en-us/graph/api/planview-delete-categories?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# categoryDefinition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A named category that can be applied to [tasks](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) in a [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta). It has no defaults beyond the universal property set.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Read plan categories](https://learn.microsoft.com/en-us/graph/planview-list-categories?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) | Read a plan with its category definitions expanded. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capabilities | [categoryDefinitionCapability](https://learn.microsoft.com/en-us/graph/api/categorydefinitioncapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| displayName | String | Name of the category. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/entity?view=graph-rest-beta) |

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
