<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistrationsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# fileStorageContainerTypeRegistrationSettings resource type

Namespace: microsoft.graph

Represents the settings associated with a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0). Some of these settings can be read-only, depending on the [settings of the fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypesettings?view=graph-rest-1.0) that define which settings are overridable.

Note

Some values are used when a **fileStorageContainer** is created but aren't affected if the settings are modified afterwards. For example, **maxStoragePerContainerInBytes**.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isDiscoverabilityEnabled | Boolean | Indicates whether items from containers are surfaced in experiences such as **My Activity** or Microsoft 365. |
| isItemVersioningEnabled | Boolean | Indicates whether item versioning is enabled. |
| isOfficeRestricted | Boolean | Indicates whether Office apps \(Word, Excel, and PowerPoint\) for desktop and web are restricted for containers of this container type. |
| isSearchEnabled | Boolean | Indicates whether search is enabled. |
| isSharingRestricted | Boolean | Only the manager and owner can share files in the container if restricted sharing is enabled. |
| itemMajorVersionLimit | Int64 | Maximum number of versions. Versioning must be enabled \(`"isItemVersioningEnabled"=true`\). |
| maxStoragePerContainerInBytes | Int64 | Controls maximum storage in bytes. |
| sharingCapability | sharingCapabilities | Sharing capabilities permitted for containers. The possible values are: `disabled`, `externalUserSharingOnly`, `externalUserAndGuestSharing`, `existingExternalUserSharingOnly`, `unknownFutureValue`. Can always be updated. |
| urlTemplate | String | Pattern used to redirect files. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fileStorageContainerTypeRegistrationSettings",
  "isDiscoverabilityEnabled": "Boolean",
  "isItemVersioningEnabled": "Boolean",
  "isOfficeRestricted": "Boolean",
  "isSearchEnabled": "Boolean",
  "isSharingRestricted": "Boolean",
  "itemMajorVersionLimit": "Int64",
  "maxStoragePerContainerInBytes": "Int64",
  "sharingCapability": "String",
  "urlTemplate": "String"
}
```
