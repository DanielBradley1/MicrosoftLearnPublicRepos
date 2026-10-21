<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# contentLink resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A URL with a display label, attached to a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) or [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta). `displayName` is the label and `webUrl` is the destination URL, both returned by default; preview, icon, and content-type metadata are opt-in.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/task-list-links?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) collection | Get a list of the contentLink objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/task-post-links?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) | Create a new contentLink object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/contentlink-get?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) | Read the properties and relationships of [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/contentlink-update?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) | Update the properties of a contentLink object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capabilities | [contentLinkCapability](https://learn.microsoft.com/en-us/graph/api/resources/contentlinkcapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who created the entity. Read-only. |
| displayName | String | Display label for the link. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who last modified the entity. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the entity was last modified. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| linkType | contentLinkType | Type of content the link points to. The possible values are: `documentReference`, `webReference`, `unknownFutureValue`. |
| webUrl | String | URL the link points to. |

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
