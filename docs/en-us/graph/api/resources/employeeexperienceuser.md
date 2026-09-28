<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/employeeexperienceuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# employeeExperienceUser resource type

Namespace: microsoft.graph

Represents a container that exposes navigation properties for the employee experience resources of a user.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List assigned roles](https://learn.microsoft.com/en-us/graph/api/employeeexperienceuser-list-assignedroles?view=graph-rest-1.0) | [engagementRole](https://learn.microsoft.com/en-us/graph/api/resources/engagementrole?view=graph-rest-1.0) collection | Get a list of all the [roles](https://learn.microsoft.com/en-us/graph/api/resources/engagementrole?view=graph-rest-1.0) assigned to a user in Viva Engage. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignedRoles | [engagementRole](https://learn.microsoft.com/en-us/graph/api/resources/engagementrole?view=graph-rest-1.0) collection | Represents the collection of Viva Engage roles assigned to a user. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.employeeExperienceUser"
}
```
