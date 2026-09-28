<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# store resource type

Namespace: microsoft.graph.termStore

Represents a taxonomy term store.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/termstore-list-groups?view=graph-rest-1.0) | [microsoft.graph.termStore.group](https://learn.microsoft.com/en-us/graph/api/resources/termstore-group?view=graph-rest-1.0) collection | Get the groups available in the term store object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/termstore-store-get?view=graph-rest-1.0) | [microsoft.graph.termStore.store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0) | Read the properties and relationships of a term store object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/termstore-store-update?view=graph-rest-1.0) | [microsoft.graph.termStore.store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0) | Update the properties of a term store object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultLanguageTag | String | Default language of the term store. |
| id | String | Unique identifier of the term store. Read-only. |
| languageTags | String collection | List of languages for the term store. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| groups | [microsoft.graph.termStore.group](https://learn.microsoft.com/en-us/graph/api/resources/termstore-group?view=graph-rest-1.0) collection | Collection of all groups available in the term store. |
| sets | [microsoft.graph.termStore.set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) collection | Collection of all sets available in the term store. This relationship can only be used to load a specific term set. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.termStore.store",
  "id": "String (identifier)",
  "defaultLanguageTag": "String",
  "languageTags": [
    "String"
  ]  
}
```
