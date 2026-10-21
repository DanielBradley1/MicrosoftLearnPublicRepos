<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# checklistItemV4 resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A checklist item on a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta), consisting of a title and a checked/unchecked state. `isChecked` is the only default beyond the universal `displayName`.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/task-list-checklist?view=graph-rest-beta) | [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta) collection | Get a list of the checklistItemV4 objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/task-post-checklist?view=graph-rest-beta) | [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta) | Create a new checklistItemV4 object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/checklistitemv4-get?view=graph-rest-beta) | [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta) | Read the properties and relationships of [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/checklistitemv4-update?view=graph-rest-beta) | [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta) | Update the properties of a checklistItemV4 object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capabilities | [checklistCapability](https://learn.microsoft.com/en-us/graph/api/resources/checklistcapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| completedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who checked the checklist item. |
| completedDateTime | DateTimeOffset | Date and time the checklist item was checked. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who created the entity. Read-only. |
| displayName | String | Title of the checklist item. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| isChecked | Boolean | Indicates whether the checklist item is checked \(completed\). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who last modified the entity. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the entity was last modified. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.checklistItemV4",
  "id": "String (identifier)",
  "displayName": "String",
  "isChecked": "Boolean",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "completedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "completedDateTime": "String (timestamp)",
  "capabilities": {
    "@odata.type": "microsoft.graph.checklistCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
