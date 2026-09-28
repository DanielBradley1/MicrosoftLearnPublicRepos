<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedEBookCategory resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for a single Intune eBook category.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedEBookCategories](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebookcategory-list?view=graph-rest-beta) | [managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory?view=graph-rest-beta) collection | List properties and relationships of the [managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory?view=graph-rest-beta) objects. |
| [Get managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebookcategory-get?view=graph-rest-beta) | [managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory?view=graph-rest-beta) | Read properties and relationships of the [managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory?view=graph-rest-beta) object. |
| [Create managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebookcategory-create?view=graph-rest-beta) | [managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory?view=graph-rest-beta) | Create a new [managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory?view=graph-rest-beta) object. |
| [Delete managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebookcategory-delete?view=graph-rest-beta) | None | Deletes a [managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory?view=graph-rest-beta). |
| [Update managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebookcategory-update?view=graph-rest-beta) | [managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory?view=graph-rest-beta) | Update the properties of a [managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key of the entity. |
| displayName | String | The name of the eBook category. |
| lastModifiedDateTime | DateTimeOffset | The date and time the ManagedEBookCategory was last modified. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedEBookCategory",
  "id": "String (identifier)",
  "displayName": "String",
  "lastModifiedDateTime": "String (timestamp)"
}
```
