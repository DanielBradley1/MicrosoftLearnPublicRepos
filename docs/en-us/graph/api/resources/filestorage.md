<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/filestorage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# fileStorage resource type

Namespace: microsoft.graph

Represents the structure of active and deleted [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) objects.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List containers](https://learn.microsoft.com/en-us/graph/api/filestorage-list-containers?view=graph-rest-1.0) | [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) collection | Get a list of the [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) objects and their properties. |
| [Remove deleted containers](https://learn.microsoft.com/en-us/graph/api/filestorage-delete-deletedcontainers?view=graph-rest-1.0) | [fileStorage](https://learn.microsoft.com/en-us/graph/api/resources/filestorage?view=graph-rest-1.0) collection | Delete the [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) objects and their properties. |
| [List container types](https://learn.microsoft.com/en-us/graph/api/filestorage-list-containertypes?view=graph-rest-1.0) | [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) collection | Get a list of the [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) objects and their properties for the current tenant. |
| [Create file storage container type](https://learn.microsoft.com/en-us/graph/api/filestorage-post-containertypes?view=graph-rest-1.0) | [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) | Create a new [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) in the owning tenant. |
| [List container type registrations](https://learn.microsoft.com/en-us/graph/api/filestorage-list-containertyperegistrations?view=graph-rest-1.0) | [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) collection | Get a list of the [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) objects and their properties. |
| [Create file storage container type registration](https://learn.microsoft.com/en-us/graph/api/filestorage-post-containertyperegistrations?view=graph-rest-1.0) | [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) | Create or replace a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) object. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| containers | [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) collection | The collection of active **fileStorageContainer** resources. |
| containerTypeRegistrations | [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) collection | The collection of **fileStorageContainerTypeRegistration** resources. |
| containerTypes | [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) collection | The collection of **fileStorageContainerType** resources. |
| deletedContainers | [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) collection | The collection of deleted **fileStorageContainer** resources. |

## JSON representation

The following JSON representation shows the response.

```json
{
  "@odata.type": "#microsoft.graph.fileStorage"
}
```
