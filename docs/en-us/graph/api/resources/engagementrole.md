<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/engagementrole?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-22 -->

# engagementRole resource type

Namespace: microsoft.graph

Represents a predefined Viva Engage role. Each role includes a unique identifier and display name and can be assigned to one or more users within the platform.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/employeeexperience-list-roles?view=graph-rest-1.0) | [engagementRole](https://learn.microsoft.com/en-us/graph/api/resources/engagementrole?view=graph-rest-1.0) collection | Get a list of all the [roles](https://learn.microsoft.com/en-us/graph/api/resources/engagementrole?view=graph-rest-1.0) that can be assigned in Viva Engage. |
| [List members](https://learn.microsoft.com/en-us/graph/api/engagementrole-list-members?view=graph-rest-1.0) | [engagementRoleMember](https://learn.microsoft.com/en-us/graph/api/resources/engagementrolemember?view=graph-rest-1.0) collection | Get a list of users with assigned [roles](https://learn.microsoft.com/en-us/graph/api/resources/engagementrole?view=graph-rest-1.0) in Viva Engage. |
| [List assigned roles](https://learn.microsoft.com/en-us/graph/api/employeeexperienceuser-list-assignedroles?view=graph-rest-1.0) | [engagementRole](https://learn.microsoft.com/en-us/graph/api/resources/engagementrole?view=graph-rest-1.0) | Get a list of all the [roles](https://learn.microsoft.com/en-us/graph/api/resources/engagementrole?view=graph-rest-1.0) assigned to a user in Viva Engage. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the role. |
| id | String | The unique identifier of the role. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [engagementRoleMember](https://learn.microsoft.com/en-us/graph/api/resources/engagementrolemember?view=graph-rest-1.0) collection | Users that have this role assigned. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.engagementRole",
  "displayName": "String",
  "id": "String (identifier)"
}
```
