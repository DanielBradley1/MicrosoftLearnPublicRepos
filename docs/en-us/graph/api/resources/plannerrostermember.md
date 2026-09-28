<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerrostermember?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# plannerRosterMember resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a member of a [plannerRoster](https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List roster's members](https://learn.microsoft.com/en-us/graph/api/plannerroster-list-members?view=graph-rest-beta) | [plannerRosterMember](https://learn.microsoft.com/en-us/graph/api/resources/plannerrostermember?view=graph-rest-beta) collection | Get a list of the [plannerRosterMember](https://learn.microsoft.com/en-us/graph/api/resources/plannerrostermember?view=graph-rest-beta) objects and their properties. |
| [Add a member to roster](https://learn.microsoft.com/en-us/graph/api/plannerroster-post-members?view=graph-rest-beta) | [plannerRosterMember](https://learn.microsoft.com/en-us/graph/api/resources/plannerrostermember?view=graph-rest-beta) | Create a new [plannerRosterMember](https://learn.microsoft.com/en-us/graph/api/resources/plannerrostermember?view=graph-rest-beta) object. |
| [Get roster's member](https://learn.microsoft.com/en-us/graph/api/plannerrostermember-get?view=graph-rest-beta) | [plannerRosterMember](https://learn.microsoft.com/en-us/graph/api/resources/plannerrostermember?view=graph-rest-beta) | Read the properties and relationships of a [plannerRosterMember](https://learn.microsoft.com/en-us/graph/api/resources/plannerrostermember?view=graph-rest-beta) object. |
| [Remove a member from roster](https://learn.microsoft.com/en-us/graph/api/plannerrostermember-delete?view=graph-rest-beta) | None | Deletes a [plannerRosterMember](https://learn.microsoft.com/en-us/graph/api/resources/plannerrostermember?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the **plannerRosterMember**. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| roles | String collection | Additional roles associated with the **PlannerRosterMember**, which determines permissions of the member in the **plannerRoster**. Currently there are no available roles to assign, and every member has full control over the contents of the **plannerRoster**. |
| tenantId | String | Identifier of the tenant the user belongs to. Currently only the users from the same tenant can be added to a **plannerRoster**. |
| userId | String | Identifier of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerRosterMember",
  "id": "String (identifier)",
  "userId": "String",
  "tenantId": "String",
  "roles": []
}
```
