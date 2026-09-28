<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRoleDefinition resource type

Namespace: microsoft.graph

A role definition is a collection of permissions in Microsoft Entra listing the operations that can be performed and the resources against which they can performed.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roledefinitions?view=graph-rest-1.0) | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) collection | Read a list of unifiedRoleDefinition objects, and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedroledefinition-get?view=graph-rest-1.0) | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) | Read the properties of a unifiedRoleDefinition object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roledefinitions?view=graph-rest-1.0) | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) | Create a unifiedRoleDefinition object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/unifiedroledefinition-update?view=graph-rest-1.0) | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) | Update a unifiedRoleDefinition object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/unifiedroledefinition-delete?view=graph-rest-1.0) | None | Delete a unifiedRoleDefinition object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description for the unifiedRoleDefinition. Read-only when **isBuiltIn** is `true`. |
| displayName | String | The display name for the unifiedRoleDefinition. Read-only when **isBuiltIn** is `true`. Required. Supports $filter \(`eq`, `in`\). |
| id | String | The unique identifier for the role definition. Key, not nullable, Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Supports $filter \(`eq`, `in`\). |
| isBuiltIn | Boolean | Flag indicating whether the role definition is part of the default set included in Microsoft Entra or a custom definition. Read-only. Supports $filter \(`eq`, `in`\). |
| isEnabled | Boolean | Flag indicating whether the role is enabled for assignment. If `false` the role is not available for assignment. Read-only when **isBuiltIn** is true. |
| resourceScopes | String collection | List of the scopes or permissions the role definition applies to. Currently only `/` is supported. Read-only when **isBuiltIn** is true. **DO NOT USE. This will be deprecated soon. Attach scope to role assignment.** |
| rolePermissions | [unifiedRolePermission](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolepermission?view=graph-rest-1.0) collection | List of permissions included in the role. Read-only when **isBuiltIn** is `true`. Required. |
| templateId | String | Custom template identifier that can be set when **isBuiltIn** is `false` but is read-only when **isBuiltIn** is `true`. This identifier is typically used if one needs an identifier to be the same across different directories. |
| version | String | Indicates version of the role definition. Read-only when **isBuiltIn** is `true`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| inheritsPermissionsFrom | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) collection | Read-only collection of role definitions that the given role definition inherits from. Only Microsoft Entra built-in roles \(**isBuiltIn** is `true`\) support this attribute. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleDefinition",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isBuiltIn": "Boolean",
  "isEnabled": "Boolean",
  "resourceScopes": [
    "String"
  ],
  "rolePermissions": [
    {
      "@odata.type": "microsoft.graph.unifiedRolePermission"
    }
  ],
  "templateId": "String",
  "version": "String"
}
```
