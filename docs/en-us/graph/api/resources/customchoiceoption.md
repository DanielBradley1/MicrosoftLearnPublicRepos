<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customchoiceoption?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# customChoiceOption resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A selectable option for a single-choice or multiple-choice [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta), contained under its `choiceOptions` collection.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/customfielddefinition-list-choiceoptions?view=graph-rest-beta) | [customChoiceOption](https://learn.microsoft.com/en-us/graph/api/resources/customchoiceoption?view=graph-rest-beta) collection | Get a list of the customChoiceOption objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/customfielddefinition-post-choiceoptions?view=graph-rest-beta) | [customChoiceOption](https://learn.microsoft.com/en-us/graph/api/resources/customchoiceoption?view=graph-rest-beta) | Create a new customChoiceOption object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/customchoiceoption-get?view=graph-rest-beta) | [customChoiceOption](https://learn.microsoft.com/en-us/graph/api/resources/customchoiceoption?view=graph-rest-beta) | Read the properties and relationships of [customChoiceOption](https://learn.microsoft.com/en-us/graph/api/resources/customchoiceoption?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/customchoiceoption-update?view=graph-rest-beta) | [customChoiceOption](https://learn.microsoft.com/en-us/graph/api/resources/customchoiceoption?view=graph-rest-beta) | Update the properties of a customChoiceOption object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/customfielddefinition-delete-choiceoptions?view=graph-rest-beta) | None | Delete a customChoiceOption object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display text of the choice option. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customChoiceOption",
  "id": "String (identifier)",
  "displayName": "String",
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
