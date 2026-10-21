<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# dependency resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An edge that expresses a dependency constraint between two items \(for example, two [tasks](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta)\) in a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta). All four endpoint properties \(`sourceItemType`, `sourceItemId`, `targetItemType`, `targetItemId`\) are returned by default because they are the entity's intrinsic content.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/plan-list-dependencies?view=graph-rest-beta) | [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta) collection | Get a list of the dependency objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/plan-post-dependencies?view=graph-rest-beta) | [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta) | Create a new dependency object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/dependency-get?view=graph-rest-beta) | [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta) | Read the properties and relationships of [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/dependency-update?view=graph-rest-beta) | [dependency](https://learn.microsoft.com/en-us/graph/api/resources/dependency?view=graph-rest-beta) | Update the properties of a dependency object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/plan-delete-dependencies?view=graph-rest-beta) | None | Delete a dependency object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| archivalInfo | [plannerArchivalInfo](https://learn.microsoft.com/en-us/graph/api/resources/plannerarchivalinfo?view=graph-rest-beta) | Information about whether the entity is archived, and when it was archived. |
| constraint | dependencyType | The kind of dependency constraint between the source and target items. The possible values are: `sourceFinishDrivesTargetStart`, `sourceStartDrivesTargetStart`, `sourceFinishDrivesTargetFinish`, `targetStartDrivesSourceFinish`, `unknownFutureValue`. |
| creationInfo | [creationInfo](https://learn.microsoft.com/en-us/graph/api/resources/creationinfo?view=graph-rest-beta) | Read-only creation metadata for the entity. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who last modified the entity. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the entity was last modified. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| sourceItemId | String | ID of the source item in the dependency. |
| targetItemId | String | ID of the target item in the dependency. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.dependency",
  "id": "String (identifier)",
  "sourceItemId": "String",
  "targetItemId": "String",
  "constraint": "String",
  "creationInfo": {
    "@odata.type": "microsoft.graph.creationInfo"
  },
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
