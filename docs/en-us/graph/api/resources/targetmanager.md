<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/targetmanager?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-04 -->

# targetManager resource type

Namespace: microsoft.graph

Used in an access package assignment policy, this type inherits from [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) and indicates the manager, including indirect managers of a user may request on behalf of that user.

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
