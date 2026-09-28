<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# roleDefinition resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The Role Definition resource. The role definition is the foundation of role based access in Intune. The role combines an Intune resource such as a Mobile App and associated role permissions such as Create or Read for the resource. There are two types of roles, built-in and custom. Built-in roles cannot be modified. Both built-in roles and custom roles must have assignments to be enforced. Create custom roles if you want to define a role that allows any of the available resources and role permissions to be combined into a single role.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List roleDefinitions](https://learn.microsoft.com/en-us/graph/api/intune-rbac-roledefinition-list?view=graph-rest-1.0) | [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) collection | List properties and relationships of the [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) objects. |
| [Get roleDefinition](https://learn.microsoft.com/en-us/graph/api/intune-rbac-roledefinition-get?view=graph-rest-1.0) | [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) | Read properties and relationships of the [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) object. |
| [Create roleDefinition](https://learn.microsoft.com/en-us/graph/api/intune-rbac-roledefinition-create?view=graph-rest-1.0) | [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) | Create a new [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) object. |
| [Delete roleDefinition](https://learn.microsoft.com/en-us/graph/api/intune-rbac-roledefinition-delete?view=graph-rest-1.0) | None | Deletes a [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0). |
| [Update roleDefinition](https://learn.microsoft.com/en-us/graph/api/intune-rbac-roledefinition-update?view=graph-rest-1.0) | [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) | Update the properties of a [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This is read-only and automatically generated. |
| displayName | String | Display Name of the Role definition. |
| description | String | Description of the Role definition. |
| rolePermissions | [rolePermission](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolepermission?view=graph-rest-1.0) collection | List of Role Permissions this role is allowed to perform. These must match the actionName that is defined as part of the rolePermission. |
| isBuiltIn | Boolean | Type of Role. Set to True if it is built-in, or set to False if it is a custom role definition. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| roleAssignments | [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment?view=graph-rest-1.0) collection | List of Role assignments for this role definition. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.roleDefinition",
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
