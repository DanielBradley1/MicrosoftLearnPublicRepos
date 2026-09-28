<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/assignedplacemode?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# assignedPlaceMode resource type

Namespace: microsoft.graph

Defines the user to whom a [desk](https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0) is assigned. This mode is only supported for **desk** objects. All the assigned **desk** objects must be assigned to a user. Either property can be used to assign a **desk** to a user.

Inherits from [placeMode](https://learn.microsoft.com/en-us/graph/api/resources/placemode?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedUserEmailAddress | String | The email address of the user to whom the desk is assigned. |
| assignedUserId | String | The user ID of the user to whom the desk is assigned. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.assignedPlaceMode",
  "assignedUserEmailAddress": "String",
  "assignedUserId": "String"
}
```
