<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/admintodo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# adminTodo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Company-wide configuration for Microsoft Todo.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/admintodo-get?view=graph-rest-beta) | [adminTodo](https://learn.microsoft.com/en-us/graph/api/resources/admintodo?view=graph-rest-beta) | Read the properties and relationships of a [adminTodo](https://learn.microsoft.com/en-us/graph/api/resources/admintodo?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/admintodo-update?view=graph-rest-beta) | [adminTodo](https://learn.microsoft.com/en-us/graph/api/resources/admintodo?view=graph-rest-beta) | Update the properties and relationships of a [adminTodo](https://learn.microsoft.com/en-us/graph/api/resources/admintodo?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique ID. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| settings | [todoSettings](https://learn.microsoft.com/en-us/graph/api/resources/todosettings?view=graph-rest-beta) | Company-wide settings for Microsoft Todo. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.adminTodo",
  "id": "String (identifier)",
  "settings": {
    "@odata.type": "todoSettings"
  }
}
```
