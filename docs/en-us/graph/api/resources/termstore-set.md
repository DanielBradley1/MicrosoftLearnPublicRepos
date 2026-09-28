<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# set resource type

Namespace: microsoft.graph.termStore

Represents the set used in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). The set represents a unit which contains a collection of hierarchical terms. A [group](https://learn.microsoft.com/en-us/graph/api/resources/termstore-group?view=graph-rest-1.0) can contain multiple sets.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List sets](https://learn.microsoft.com/en-us/graph/api/termstore-group-list-sets?view=graph-rest-1.0) | collection [microsoft.graph.termStore.set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) | Returns a list of sets contained within a [group](https://learn.microsoft.com/en-us/graph/api/resources/termstore-group?view=graph-rest-1.0) of a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Create set](https://learn.microsoft.com/en-us/graph/api/termstore-set-post?view=graph-rest-1.0) | [microsoft.graph.termStore.set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) | Create a new set object in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Create term](https://learn.microsoft.com/en-us/graph/api/termstore-term-post?view=graph-rest-1.0) | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) | Create a new [term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) object in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Get set](https://learn.microsoft.com/en-us/graph/api/termstore-set-get?view=graph-rest-1.0) | [microsoft.graph.termStore.set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) | Get a set object in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Get term](https://learn.microsoft.com/en-us/graph/api/termstore-term-get?view=graph-rest-1.0) | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) | Get a [term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) object in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Update set](https://learn.microsoft.com/en-us/graph/api/termstore-set-update?view=graph-rest-1.0) | [microsoft.graph.termStore.set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) | Update the properties of a set object in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Delete set](https://learn.microsoft.com/en-us/graph/api/termstore-set-delete?view=graph-rest-1.0) | None | Deletes a set object in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Date and time of set creation. Read-only. |
| description | String | Description that gives details on the term usage. |
| id | String | Unique identifier. Read-only. |
| localizedNames | [microsoft.graph.termStore.localizedName](https://learn.microsoft.com/en-us/graph/api/resources/termstore-localizedname?view=graph-rest-1.0) collection | Name of the set for each languageTag. |
| properties | [microsoft.graph.keyValue](https://learn.microsoft.com/en-us/graph/api/resources/keyvalue?view=graph-rest-1.0) collection | Custom properties for the set. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| children | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) collection | Children terms of set in term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| parentGroup | [microsoft.graph.termStore.group](https://learn.microsoft.com/en-us/graph/api/resources/termstore-group?view=graph-rest-1.0) | The parent [group](https://learn.microsoft.com/en-us/graph/api/resources/termstore-group?view=graph-rest-1.0) that contains the set. |
| relations | [microsoft.graph.termStore.relation](https://learn.microsoft.com/en-us/graph/api/resources/termstore-relation?view=graph-rest-1.0) collection | Indicates which terms have been pinned or reused directly under the set. |
| terms | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) collection | All the terms under the set. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.termStore.set",
  "id": "String (identifier)",
  "localizedNames": [
    {
      "@odata.type": "microsoft.graph.termStore.localizedName"
    }
  ],
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "properties": [
    {
      "@odata.type": "microsoft.graph.termStore.keyValue"
    }
  ]
}
```
