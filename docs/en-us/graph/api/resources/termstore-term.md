<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# term resource type

Namespace: microsoft.graph.termStore

Represents a term used in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). A term can be used to represent an object which can then be used as a metadata to tag content. Multiple terms can be organized in a hierarchical manner within a [set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List children](https://learn.microsoft.com/en-us/graph/api/termstore-term-list-children?view=graph-rest-1.0) | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) collection | Get the first level children of a term in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [List relations](https://learn.microsoft.com/en-us/graph/api/termstore-term-list-relations?view=graph-rest-1.0) | [microsoft.graph.termStore.relation](https://learn.microsoft.com/en-us/graph/api/resources/termstore-relation?view=graph-rest-1.0) collection | Get the relations of a term in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Create relation](https://learn.microsoft.com/en-us/graph/api/termstore-relation-post?view=graph-rest-1.0) | [microsoft.graph.termStore.relation](https://learn.microsoft.com/en-us/graph/api/resources/termstore-relation?view=graph-rest-1.0) | Create a new relation for a term or a [set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Create term](https://learn.microsoft.com/en-us/graph/api/termstore-term-post?view=graph-rest-1.0) | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) | Create a new term object in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Get term](https://learn.microsoft.com/en-us/graph/api/termstore-term-get?view=graph-rest-1.0) | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) | Read the properties and relationships of a term object in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Update term](https://learn.microsoft.com/en-us/graph/api/termstore-term-update?view=graph-rest-1.0) | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) | Update the properties of a term object in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Delete term](https://learn.microsoft.com/en-us/graph/api/termstore-term-delete?view=graph-rest-1.0) | None | Delete a term object in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Date and time of term creation. Read-only. |
| descriptions | [microsoft.graph.termStore.localizedDescription](https://learn.microsoft.com/en-us/graph/api/resources/termstore-localizeddescription?view=graph-rest-1.0) collection | Description about term that is dependent on the languageTag. |
| id | String | Unique identifier of term. Read-Only. |
| labels | [microsoft.graph.termStore.localizedLabel](https://learn.microsoft.com/en-us/graph/api/resources/termstore-localizedlabel?view=graph-rest-1.0) collection | Label metadata for a term. |
| lastModifiedDateTime | DateTimeOffset | Last date and time of term modification. Read-only. |
| properties | [microsoft.graph.keyValue](https://learn.microsoft.com/en-us/graph/api/resources/keyvalue?view=graph-rest-1.0) collection | Collection of properties on the term. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| children | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) collection | Children of current term. |
| relations | [microsoft.graph.termStore.relation](https://learn.microsoft.com/en-us/graph/api/resources/termstore-relation?view=graph-rest-1.0) collection | To indicate which terms are related to the current term as either pinned or reused. |
| set | [microsoft.graph.termStore.set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) | The [set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) in which the term is created. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.termStore.term",
  "id": "String (identifier)",
  "labels": [
    {
      "@odata.type": "microsoft.graph.termStore.localizedLabel"
    }
  ],
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "descriptions": [
    {
      "@odata.type": "microsoft.graph.termStore.localizedDescription"
    }
  ],
  "properties": [
    {
      "@odata.type": "microsoft.graph.keyValue"
    }
  ]
}
```
