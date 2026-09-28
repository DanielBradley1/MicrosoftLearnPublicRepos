<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-21 -->

# groupResource resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) resource in PIM for groups. This entity extends [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-resources?view=graph-rest-beta) | [groupResource](https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-beta) collection | Retrieve a list of [groupResource](https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-beta) objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/groupresource-get?view=graph-rest-beta) | [groupResource](https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-beta) | Read the properties of a [groupResource](https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Indicates the identifier of the group. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| deletedDateTime | DateTimeOffset | `null`. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "deletedDateTime": "String (timestamp)"
}
```
