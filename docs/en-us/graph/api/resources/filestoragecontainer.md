<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# fileStorageContainer resource type

Namespace: microsoft.graph

Represents a location where multiple users or a group of users can store files and access them via an application. All file system objects in a **fileStorageContainer** are returned as [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) resources.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/filestorage-list-containers?view=graph-rest-1.0) | [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) | Get a list of [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) objects that are accessible to a caller. |
| [Create](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-post?view=graph-rest-1.0) | [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) | Create a new [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-get?view=graph-rest-1.0) | [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) | Read the properties and relationships of a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-update?view=graph-rest-1.0) | [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) | Update the properties of a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/filestorage-delete-containers?view=graph-rest-1.0) | None | Delete a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object. |
| [Activate](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-activate?view=graph-rest-1.0) | None | Activate a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object. |
| [Restore deleted container](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-restore?view=graph-rest-1.0) | [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) | Restore a deleted [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object. |
| [Remove deleted containers](https://learn.microsoft.com/en-us/graph/api/filestorage-delete-deletedcontainers?view=graph-rest-1.0) | None | Remove a deleted [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-permanentdelete?view=graph-rest-1.0) | None | Permanently delete a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object. |
| [Get drive](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-get-drive?view=graph-rest-1.0) | [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) | Get the drive resource from a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object. |
| [List permissions](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-list-permissions?view=graph-rest-1.0) | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) collection | List permissions on a fileStorageContainer. |
| [Get permission](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-get-permissions?view=graph-rest-1.0) | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) | Get a specific [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) from a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object. |
| [Add permissions](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-post-permissions?view=graph-rest-1.0) | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) | Add permission to a fileStorageContainer. |
| [Update permissions](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-update-permissions?view=graph-rest-1.0) | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) | Update permission on a fileStorageContainer. |
| [Delete permissions](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-delete-permissions?view=graph-rest-1.0) | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) | Delete permission from a fileStorageContainer. |
| [Upsert permissions](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-patch-permissions?view=graph-rest-1.0) | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) collection | Upsert \(create or update\) up to 10 [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) objects on a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) in a single request. |
| [List custom property](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-list-customproperty?view=graph-rest-1.0) | [filestoragecontainercustompropertyvalue](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainercustompropertyvalue?view=graph-rest-1.0) | List custom properties of the fileStorageContainer. |
| [Add custom property](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-post-customproperty?view=graph-rest-1.0) | [filestoragecontainercustompropertyvalue](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainercustompropertyvalue?view=graph-rest-1.0) | Add custom property to the fileStorageContainer. |
| [Update custom property](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-update-customproperty?view=graph-rest-1.0) | [filestoragecontainercustompropertyvalue](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainercustompropertyvalue?view=graph-rest-1.0) | Update custom property on a fileStorageContainer. |
| [Delete custom property](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-delete-customproperty?view=graph-rest-1.0) | [filestoragecontainercustompropertyvalue](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainercustompropertyvalue?view=graph-rest-1.0) | Delete custom property from a fileStorageContainer. |
| [List columns](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-list-columns?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) collection | Get the collection of columns represented as [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) resources in a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [Create column](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-post-columns?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) | Create a column for a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) that specifies a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0). |
| [Get column](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-get-column?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) | Get the properties of a column represented as a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) in a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [Update column](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-update-column?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) | Update an existing column represented as a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) in a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [Delete column](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-delete-column?view=graph-rest-1.0) | None | Delete a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) from a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [Upsert columns](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-patch-columns?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) collection | Upsert \(create or update\) up to 20 [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) objects on a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) in a single request. |
| [Update recycle bin settings](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-update-recyclebinsettings?view=graph-rest-1.0) | [recyclebinsettings](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinsettings?view=graph-rest-1.0) | Update recycleBin settings for a fileStorageContainer. |
| [Delete recycle bin items](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-delete-recyclebinitem?view=graph-rest-1.0) | None | Delete recycle bin items from a fileStorageContainer. |
| [Restore recycle bin items](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-restore-recyclebinitem?view=graph-rest-1.0) | [recycleBinItem](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0) collection | Restore recycle bin items in a fileStorageContainer. |
| [Get recycle bin items](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-list-recyclebinitem?view=graph-rest-1.0) | [recycleBinItem](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0) collection | List recycle bin items in a fileStorageContainer. |
| [Lock](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-lock?view=graph-rest-1.0) | None | Lock a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [Unlock](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-unlock?view=graph-rest-1.0) | None | Unlock a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [Create migration job](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-post-migrationjobs?view=graph-rest-1.0) | [sharePointMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjob?view=graph-rest-1.0) | Create a new [sharePointMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjob?view=graph-rest-1.0) object that is scheduled to run at a later time to migrate content from an intermediary storage to the target [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [Provision migration containers](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-provisionmigrationcontainers?view=graph-rest-1.0) | [sharePointMigrationContainerInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationcontainerinfo?view=graph-rest-1.0) | Provision SharePoint-managed Azure blob containers as temporary storage for migration content and metadata. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedSensitivityLabel | [assignedLabel](https://learn.microsoft.com/en-us/graph/api/resources/assignedlabel?view=graph-rest-1.0) | Sensitivity label assigned to the **fileStorageContainer**. Read-write. |
| containerTypeId | Guid | Container type ID of the **fileStorageContainer**. For details about container types, see [Container Types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). Each container must have only one container type. Read-only. |
| createdDateTime | DateTimeOffset | Date and time of the **fileStorageContainer** creation. Read-only. |
| customProperties | [fileStorageContainerCustomPropertyDictionary](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainercustompropertydictionary?view=graph-rest-1.0) | Custom property collection for the **fileStorageContainer**. Read-write. |
| description | String | Provides a user-visible description of the **fileStorageContainer**. Read-write. |
| displayName | String | The display name of the **fileStorageContainer**. Read-write. |
| id | String | The unique stable identifier of the **filerStorageContainer**. Read-only. |
| lockState | siteLockState | Indicates the lock state of the **fileStorageContainer**. The possible values are `unlocked` and `lockedReadOnly`. Read-only. |
| settings | [fileStorageContainerSettings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainersettings?view=graph-rest-1.0) | Settings associated with a **fileStorageContainer**. Read-write. |
| status | fileStorageContainerStatus | Status of the **fileStorageContainer**. Containers are created as inactive and require activation. Inactive containers are subjected to automatic deletion in 24 hours. The possible values are: `inactive `, `active `. Read-only. |
| viewpoint | [fileStorageContainerViewpoint](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainerviewpoint?view=graph-rest-1.0) | Data specific to the current user. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| columns | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) collection | The set of custom structured metadata supported by the **fileStorageContainer**. Read-write. |
| drive | [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) | The drive of the resource **fileStorageContainer**. Read-only. |
| migrationJobs | [sharePointMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjob?view=graph-rest-1.0) collection | The collection of **sharePointMigrationJob** objects local to the container. Read-write. |
| permissions | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) collection | The set of permissions for users in the **fileStorageContainer**. Permission for each user is set by the **roles** property. The possible values are: `reader`, `writer`, `manager`, and `owner`. Read-write. |
| recycleBin | [recycleBin](https://learn.microsoft.com/en-us/graph/api/resources/recyclebin?view=graph-rest-1.0) | Recycle bin of the **fileStorageContainer**. Read-only. |
| sharePointGroups | [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) collection | The collection of **sharePointGroup** objects local to the container. Read-write. |

### roles property values

| Value | Description |
| :--- | :--- |
| reader | Readers can read **fileStorageContainer** metadata and the contents inside. |
| writer | Writers can read and modify **fileStorageContainer** metadata and contents inside. |
| manager | Managers can read and modify **fileStorageContainer** metadata and contents inside and manage the permissions to the container. |
| owner | Owners can read and modify **fileStorageContainer** metadata and contents inside, manage container permissions, and delete and restore containers. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fileStorageContainer",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "containerTypeId": "Guid",
  "assignedSensitivityLabel": {
    "@odata.type": "microsoft.graph.assignedLabel"
  },
  "customProperties": {
    "@odata.type": "microsoft.graph.fileStorageContainerCustomPropertyDictionary"
  },
  "viewpoint": {
    "@odata.type": "microsoft.graph.fileStorageContainerViewpoint"
  },
  "status": "String",
  "createdDateTime": "String (timestamp)",
  "settings": { "@odata.type": "microsoft.graph.fileStorageContainerSettings" }
}
```
