<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/directoryroletemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-19 -->

# directoryRoleTemplate resource type

Namespace: microsoft.graph

Note

Microsoft recommends that you use the unified RBAC API instead of this API. The unified RBAC API provides more functionality and flexibility. For more information, see [unifiedRoleDefinition resource type](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0).

Represents a directory role template. A directory role template specifies the property values of a directory role \([directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0)\). There's an associated directory role template object for each of the directory roles that may be activated in a tenant. To read a directory role or update its members, it must first be activated in the tenant. Only the Company Administrators directory role is activated by default. To activate other available directory roles, you send a POST request to the `/directoryRoles` endpoint with the ID of the directory role template on which the directory role is based specified in the **roleTemplateId** parameter of the request. Upon successful completion of this request, you can then start to read and assign members to the directory role. **Note**: A directory role template is exposed for the Users directory role. The Users directory role is implicit and isn't visible to directory clients. Every User in the tenant is assigned to this role by the infrastructure. The role is already activated. Don't use this template.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/directoryroletemplate-get?view=graph-rest-1.0) | [directoryRoleTemplate](https://learn.microsoft.com/en-us/graph/api/resources/directoryroletemplate?view=graph-rest-1.0) | Read properties and relationships of directoryRoleTemplate object. |
| [List](https://learn.microsoft.com/en-us/graph/api/directoryroletemplate-list?view=graph-rest-1.0) | [directoryRoleTemplate](https://learn.microsoft.com/en-us/graph/api/resources/directoryroletemplate?view=graph-rest-1.0) collection | Retrieve a list of directoryRoleTemplate objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description to set for the directory role. Read-only. |
| displayName | String | The display name to set for the directory role. Read-only. |
| id | String | The unique identifier for the template. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). You specify the **id** of the directory role template for the **roleTemplateId** property in the POST request activate a [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0) in a tenant. Key, Not nullable. Read-only. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "string",
  "displayName": "string",
  "id": "string (identifier)"
}
```
