<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/targetmanager?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-10 -->

# targetManager resource type

Namespace: microsoft.graph

Used in an access package assignment policy, this type inherits from [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) and indicates the manager of the target user who will receive the access package.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| managerLevel | Int32 | Manager level, between 1 and 4. The direct manager is 1. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.targetManager",
  "managerLevel": "Integer"
}
```
