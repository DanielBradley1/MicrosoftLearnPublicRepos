<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroleassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# deviceAndAppManagementRoleAssignment resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The Role Assignment resource. Role assignments tie together a role definition with members and scopes. There can be one or more role assignments per role. This applies to custom and built-in roles.

Inherits from [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceAndAppManagementRoleAssignments](https://learn.microsoft.com/en-us/graph/api/intune-rbac-deviceandappmanagementroleassignment-list?view=graph-rest-1.0) | [deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroleassignment?view=graph-rest-1.0) collection | List properties and relationships of the [deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroleassignment?view=graph-rest-1.0) objects. |
| [Get deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-deviceandappmanagementroleassignment-get?view=graph-rest-1.0) | [deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroleassignment?view=graph-rest-1.0) | Read properties and relationships of the [deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroleassignment?view=graph-rest-1.0) object. |
| [Create deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-deviceandappmanagementroleassignment-create?view=graph-rest-1.0) | [deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroleassignment?view=graph-rest-1.0) | Create a new [deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroleassignment?view=graph-rest-1.0) object. |
| [Delete deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-deviceandappmanagementroleassignment-delete?view=graph-rest-1.0) | None | Deletes a [deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroleassignment?view=graph-rest-1.0). |
| [Update deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-deviceandappmanagementroleassignment-update?view=graph-rest-1.0) | [deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroleassignment?view=graph-rest-1.0) | Update the properties of a [deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroleassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the request. This ID is assigned at when the entity is created. Read-only. Inherited from [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) |
| displayName | String | Indicates the display name of the role assignment. For example: 'Houston administrators and users'. Max length is 128 characters. Inherited from [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) |
| description | String | Indicates the description of the role assignment. For example: 'All administrators, employees and scope tags associated with the Houston office.' Max length is 1024 characters. Inherited from [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) |
| resourceScopes | String collection | Indicates the list of resource scope security group Entra IDs. For example: {dec942f4-6777-4998-96b4-522e383b08e2}. Inherited from [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) |
| members | String collection | Indicates the list of role member security group Entra IDs. For example: {dec942f4-6777-4998-96b4-522e383b08e2}. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| roleDefinition | [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) | Indicates the role definition for this role assignment. Inherited from [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementRoleAssignment",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "resourceScopes": [
    "String"
  ],
  "members": [
    "String"
  ]
}
```
