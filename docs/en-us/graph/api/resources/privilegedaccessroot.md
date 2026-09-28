<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# privilegedAccessRoot resource type

Namespace: microsoft.graph

Represents the entry point for resources related to Privileged Identity Management \(PIM\).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier for an object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| group | [privilegedAccessGroup](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroup?view=graph-rest-1.0) | A group that's governed through Privileged Identity Management \(PIM\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegedAccessRoot",
  "id": "String (identifier)"
}
```
