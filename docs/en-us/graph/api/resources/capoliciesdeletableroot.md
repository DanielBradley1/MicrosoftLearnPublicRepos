<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/capoliciesdeletableroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-27 -->

# caPoliciesDeletableRoot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a container for conditional access objects in Microsoft Entra that support soft-delete functionality.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier for a conditional access object that supports soft delete. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| namedLocations | [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-beta) collection | Read-only. Nullable. Returns a collection of the specified named locations. |
| policies | [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-beta) collection | Read-only. Nullable. Returns a collection of the specified Conditional Access policies. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.caPoliciesDeletableRoot",
  "id": "String (identifier)"
}
```
