<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/termstore-relation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# relation resource type

Namespace: microsoft.graph.termStore

Represents the relationship between [terms](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). Currently, two types of relationships are supported: **pin** and **reuse**.

In a pin relationship, a term can be pinned under a different term in a different term set. In a pinned relationship, new children to the term can only be added in the term set in which the term was created. Any change in the hierarchy under the term is reflected across the sets in which the term was pinned.

The reuse relationship is similar to the pinned relationship except that changes to the reused term can be made from any hierarchy in which the term is reused. Also, a change in hierarchy made to the reused term doesn't get reflected in the other term sets in which the term is reused.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/termstore-term-list-relations?view=graph-rest-1.0) | [microsoft.graph.termStore.relation](https://learn.microsoft.com/en-us/graph/api/resources/termstore-relation?view=graph-rest-1.0) collection | Retrieve a list of **relation** objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/termstore-relation-post?view=graph-rest-1.0) | [microsoft.graph.termStore.relation](https://learn.microsoft.com/en-us/graph/api/resources/termstore-relation?view=graph-rest-1.0) | Create a new **relation** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the relation. |
| relationship | microsoft.graph.termStore.relationType | The type of relation. The possible values are: `pin`, `reuse`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| fromTerm | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) | The from [term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) of the relation. The term from which the relationship is defined. A *null* value would indicate the relation is directly with the [set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0). |
| set | [microsoft.graph.termStore.set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) | The [set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) in which the relation is relevant. |
| toTerm | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) | The to [term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) of the relation. The term to which the relationship is defined. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.termStore.relation",
  "id": "String (identifier)",
  "relationship": "String"
}
```
