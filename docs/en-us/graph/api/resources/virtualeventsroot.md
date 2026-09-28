<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-09 -->

# virtualEventsRoot resource type

Namespace: microsoft.graph

The container for [virtual event](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0) APIs.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List webinars](https://learn.microsoft.com/en-us/graph/api/virtualeventsroot-list-webinars?view=graph-rest-1.0) | [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) collection | Get the list of all [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) objects created in a tenant. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| townhalls | [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) collection | A collection of town halls. Nullable. |
| webinars | [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) collection | A collection of webinars. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventsRoot"
}
```
