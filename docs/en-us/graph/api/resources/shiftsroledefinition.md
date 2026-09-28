<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/shiftsroledefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# shiftsRoleDefinition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A definition for a single role in a schedule in the Shifts app in Teams.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/shiftsroledefinition-get?view=graph-rest-beta) | [shiftsRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/shiftsroledefinition?view=graph-rest-beta) | Read the properties and relationships of a [shiftsRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/shiftsroledefinition?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/shiftsroledefinition-update?view=graph-rest-beta) | [shiftsRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/shiftsroledefinition?view=graph-rest-beta) | Create/Update the properties of a [shiftsRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/shiftsroledefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the role. |
| displayName | String | The display name of the role. |
| id | String | The ID of the role. |
| shiftsRolePermissions | [shiftsRolePermission](https://learn.microsoft.com/en-us/graph/api/resources/shiftsrolepermission?view=graph-rest-beta) collection | The collection of role permissions within the role. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.shiftsRoleDefinition",
  "id": "String (identifier)",
  "description": "String",
  "displayName": "String",
  "shiftsRolePermissions": [
    {
      "@odata.type": "microsoft.graph.shiftsRolePermission"
    }
  ]
}
```
