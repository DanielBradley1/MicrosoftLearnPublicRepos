<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# roleAssignment resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The Role Assignment resource. Role assignments tie together a role definition with members and scopes. There can be one or more role assignments per role. This applies to custom and built-in roles.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List roleAssignments](https://learn.microsoft.com/en-us/graph/api/intune-rbac-roleassignment-list?view=graph-rest-1.0) | [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) collection | List properties and relationships of the [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) objects. |
| [Get roleAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-roleassignment-get?view=graph-rest-1.0) | [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) | Read properties and relationships of the [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) object. |
| [Create roleAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-roleassignment-create?view=graph-rest-1.0) | [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) | Create a new [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) object. |
| [Delete roleAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-roleassignment-delete?view=graph-rest-1.0) | None | Deletes a [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0). |
| [Update roleAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-roleassignment-update?view=graph-rest-1.0) | [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) | Update the properties of a [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the request. This ID is assigned at when the entity is created. Read-only. |
| displayName | String | Indicates the display name of the role assignment. For example: 'Houston administrators and users'. Max length is 128 characters. |
| description | String | Indicates the description of the role assignment. For example: 'All administrators, employees and scope tags associated with the Houston office.' Max length is 1024 characters. |
| resourceScopes | String collection | Indicates the list of resource scope security group Entra IDs. For example: {dec942f4-6777-4998-96b4-522e383b08e2}. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| roleDefinition | [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) | Indicates the role definition for this role assignment. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.roleAssignment",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "resourceScopes": [
    "String"
  ]
}
```
