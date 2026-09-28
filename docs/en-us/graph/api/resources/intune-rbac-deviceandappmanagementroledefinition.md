<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroledefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceAndAppManagementRoleDefinition resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The Role Definition resource. The role definition is the foundation of role based access in Intune. The role combines an Intune resource such as a Mobile App and associated role permissions such as Create or Read for the resource. There are two types of roles, built-in and custom. Built-in roles cannot be modified. Both built-in roles and custom roles must have assignments to be enforced. Create custom roles if you want to define a role that allows any of the available resources and role permissions to be combined into a single role.

Inherits from [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceAndAppManagementRoleDefinitions](https://learn.microsoft.com/en-us/graph/api/intune-rbac-deviceandappmanagementroledefinition-list?view=graph-rest-1.0) | [deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroledefinition?view=graph-rest-1.0) collection | List properties and relationships of the [deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroledefinition?view=graph-rest-1.0) objects. |
| [Get deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/intune-rbac-deviceandappmanagementroledefinition-get?view=graph-rest-1.0) | [deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroledefinition?view=graph-rest-1.0) | Read properties and relationships of the [deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroledefinition?view=graph-rest-1.0) object. |
| [Create deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/intune-rbac-deviceandappmanagementroledefinition-create?view=graph-rest-1.0) | [deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroledefinition?view=graph-rest-1.0) | Create a new [deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroledefinition?view=graph-rest-1.0) object. |
| [Delete deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/intune-rbac-deviceandappmanagementroledefinition-delete?view=graph-rest-1.0) | None | Deletes a [deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroledefinition?view=graph-rest-1.0). |
| [Update deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/intune-rbac-deviceandappmanagementroledefinition-update?view=graph-rest-1.0) | [deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroledefinition?view=graph-rest-1.0) | Update the properties of a [deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroledefinition?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This is read-only and automatically generated. Inherited from [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) |
| displayName | String | Display Name of the Role definition. Inherited from [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) |
| description | String | Description of the Role definition. Inherited from [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) |
| rolePermissions | [rolePermission](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolepermission?view=graph-rest-1.0) collection | List of Role Permissions this role is allowed to perform. These must match the actionName that is defined as part of the rolePermission. Inherited from [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) |
| isBuiltIn | Boolean | Type of Role. Set to True if it is built-in, or set to False if it is a custom role definition. Inherited from [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| roleAssignments | [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) collection | List of Role assignments for this role definition. Inherited from [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementRoleDefinition",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "rolePermissions": [
    {
      "@odata.type": "microsoft.graph.rolePermission",
      "resourceActions": [
        {
          "@odata.type": "microsoft.graph.resourceAction",
          "allowedResourceActions": [
            "String"
          ],
          "notAllowedResourceActions": [
            "String"
          ]
        }
      ]
    }
  ],
  "isBuiltIn": true
}
```
