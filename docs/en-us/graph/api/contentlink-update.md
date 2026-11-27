<!-- Source: https://learn.microsoft.com/en-us/graph/api/contentlink-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# contentLink resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A URL with a display label, attached to a [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) or [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta). `displayName` is the label and `webUrl` is the destination URL, both returned by default; preview, icon, and content-type metadata are opt-in.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/plannerdelta?view=graph-rest-beta).

## Methods

To create links with their parent, use a deep insert in [Create plan](https://learn.microsoft.com/en-us/graph/planner-post-plans_v2?view=graph-rest-beta) or [Create task](https://learn.microsoft.com/en-us/graph/planner-post-tasks_v2?view=graph-rest-beta). This doesn't imply standalone create or update support.

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/task-list-links?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/contentlink?view=graph-rest-beta) collection | Get a list of the contentLink objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/contentlink-get?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/contentlink?view=graph-rest-beta) | Read the properties and relationships of [contentLink](https://learn.microsoft.com/en-us/graph/api/contentlink?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capabilities | [contentLinkCapability](https://learn.microsoft.com/en-us/graph/api/contentlinkcapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who created the entity. Read-only. |
| displayName | String | Display label for the link. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set at creation. Can't be changed afterward. Supports $select. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/entity?view=graph-rest-beta) |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who last modified the entity. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the entity was last modified. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| linkType | contentLinkType | Type of content the link points to. Required at creation and immutable afterward. The possible values are: `documentReference`, `webReference`, `unknownFutureValue`. |
| webUrl | String | URL the link points to. Required at creation and immutable afterward. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.contentLink",
  "id": "String (identifier)",
  "displayName": "String",
  "linkType": "String",
  "webUrl": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "capabilities": {
    "@odata.type": "microsoft.graph.contentLinkCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
