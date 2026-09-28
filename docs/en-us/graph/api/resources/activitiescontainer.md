<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/activitiescontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# activitiesContainer resource type

Namespace: microsoft.graph

Represents a container for different types of activity logs related to Microsoft Purview data security and governance, such as content activities.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the container. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| contentActivities | [contentActivity](https://learn.microsoft.com/en-us/graph/api/resources/contentactivity?view=graph-rest-1.0) collection | Collection of activity logs related to content processing. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.activitiesContainer",
  "id": "String (identifier)"
}
```
