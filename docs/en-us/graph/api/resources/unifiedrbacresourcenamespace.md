<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourcenamespace?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-12 -->

# unifiedRbacResourceNamespace resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the namespace of the area or service such as Microsoft Entra ID, Intune, and Exchange that defines role permissions.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rbacapplicationmultiple-list-resourcenamespaces?view=graph-rest-beta) | [unifiedRbacResourceNamespace](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourcenamespace?view=graph-rest-beta) collection | Get a list of the [unifiedRbacResourceNamespace](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourcenamespace?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedrbacresourcenamespace-get?view=graph-rest-beta) | [unifiedRbacResourceNamespace](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourcenamespace?view=graph-rest-beta) | Read the properties and relationships of an [unifiedRbacResourceNamespace](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourcenamespace?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the resource namespace that defines permissions, such as `microsoft.aad.b2c`. Required. |
| name | String | Name of the resource namespace. Typically, the same name as the **id** property, such as `microsoft.aad.b2c`. Required. Supports `$filter` \(`eq`, `startsWith`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| resourceActions | [unifiedRbacResourceAction](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourceaction?view=graph-rest-beta) collection | Operations that an authorized principal is allowed to perform. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRbacResourceNamespace",
  "id": "String (identifier)",
  "name": "String"
}
```
