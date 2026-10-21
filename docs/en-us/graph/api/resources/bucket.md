<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# bucket resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A Planner V4 bucket \(a custom column used to group [tasks](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) within a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta)\). A bucket has no defaults beyond the universal property set \(`id`, `displayName`, `createdBy`, `createdDateTime`, `lastModifiedBy`, `lastModifiedDateTime`\); it doesn't carry `archivalInfo`.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/plan-list-buckets?view=graph-rest-beta) | [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta) collection | Get a list of the bucket objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/plan-post-buckets?view=graph-rest-beta) | [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta) | Create a new bucket object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/bucket-get?view=graph-rest-beta) | [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta) | Read the properties and relationships of [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/bucket-update?view=graph-rest-beta) | [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta) | Update the properties of a bucket object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/plan-delete-buckets?view=graph-rest-beta) | None | Delete a bucket object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capabilities | [bucketCapability](https://learn.microsoft.com/en-us/graph/api/resources/bucketcapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| creationInfo | [creationInfo](https://learn.microsoft.com/en-us/graph/api/resources/creationinfo?view=graph-rest-beta) | Read-only creation metadata for the entity. |
| displayName | String | Title of the bucket. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who last modified the entity. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the entity was last modified. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| planId | String | ID of the plan that contains the bucket. Immutable after creation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bucket",
  "id": "String (identifier)",
  "displayName": "String",
  "planId": "String",
  "creationInfo": {
    "@odata.type": "microsoft.graph.creationInfo"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "capabilities": {
    "@odata.type": "microsoft.graph.bucketCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
