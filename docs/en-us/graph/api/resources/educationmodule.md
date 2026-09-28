<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# educationModule resource type

Namespace: microsoft.graph

A module is associated with a [class](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0). Represents a group of individual learning resources that are organized in a systematic way.

Only teachers or team owners can create modules. Modules contain read-only learning resources and assignments the teacher wants the student to complete.

When a **module** is created, it is in a `draft` state. Students can't see the **module** until it's published. You can change the status of a **module** by using the [publish](https://learn.microsoft.com/en-us/graph/api/educationmodule-publish?view=graph-rest-1.0) action. You can't use a PATCH request to change the **module** status.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List modules](https://learn.microsoft.com/en-us/graph/api/educationclass-list-modules?view=graph-rest-1.0) | [educationModule](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0) collection | Get an **educationModule** object collection. |
| [Create module](https://learn.microsoft.com/en-us/graph/api/educationclass-post-module?view=graph-rest-1.0) | [educationModule](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0) | Create an **educationModule** object. |
| [Get module](https://learn.microsoft.com/en-us/graph/api/educationmodule-get?view=graph-rest-1.0) | [educationModule](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0) | Read properties and relationships of an **educationModule** object. |
| [Update module](https://learn.microsoft.com/en-us/graph/api/educationmodule-update?view=graph-rest-1.0) | [educationModule](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0) | Update an **educationModule** object. |
| [Delete module](https://learn.microsoft.com/en-us/graph/api/educationmodule-delete?view=graph-rest-1.0) | None | Delete an **educationModule** object. |
| [Pin module](https://learn.microsoft.com/en-us/graph/api/educationmodule-pin?view=graph-rest-1.0) | [educationModule](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0) | Pin an **educationModule** object. |
| [Unpin module](https://learn.microsoft.com/en-us/graph/api/educationmodule-unpin?view=graph-rest-1.0) | [educationModule](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0) | Unpin an **educationModule** object. |
| [Publish module](https://learn.microsoft.com/en-us/graph/api/educationmodule-publish?view=graph-rest-1.0) | [educationModule](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0) | Change the state of an **educationModule** object from draft to published. |
| [Set up module resources folder](https://learn.microsoft.com/en-us/graph/api/educationmodule-setupresourcesfolder?view=graph-rest-1.0) | [educationModule](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0) | Create a SharePoint folder \(under predefined location\) to upload files as module resources. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The display name of the user that created the **module**. |
| createdDateTime | DateTimeOffset | Date time the **module** was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z` |
| description | String | Description of the **module**. |
| displayName | String | Name of the **module**. |
| id | String | The unique identifier for the **module**. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |
| isPinned | Boolean | Indicates whether the module is pinned or not. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The last user that modified the **module**. |
| lastModifiedDateTime | DateTimeOffset | Date time the **module** was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z` |
| resourcesFolderUrl | string | Folder URL where all the file resources for this **module** are stored. |
| status | string | Status of the **module**. You can't use a PATCH operation to update this value. The possible values are: `draft` and `published`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| resources | [educationModuleResource](https://learn.microsoft.com/en-us/graph/api/resources/educationmoduleresource?view=graph-rest-1.0) collection | Learning objects that are associated with this **module**. Only teachers can modify this list. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdBy": { "@odata.type": "microsoft.graph.identitySet" },
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isPinned": "Boolean",
  "lastModifiedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "lastModifiedDateTime": "String (timestamp)",
  "resourcesFolderUrl": "String",
  "status": "String"
}
```
