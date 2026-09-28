<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# updatableAsset resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an asset that can receive updates.

All updatable assets exist as one of the following derived types: [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) and [updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta).

Base type of [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) and [updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta).

This is an abstract type.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List updatable assets](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-list-updatableassets?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) collection | Get a list of the [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) objects and their properties. |
| [Create updatable asset group](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-post-updatableassets-updatableassetgroup?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta) | Create a new [updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta) object. |
| [Get updatable asset](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) | Read the properties and relationships of an [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) object. |
| [Delete updatable asset](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-delete?view=graph-rest-beta) | None | Delete an [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) object. |
| [Enroll in update management](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-enrollassets?view=graph-rest-beta) | None | Enroll [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) resources in update management by Windows Autopatch. |
| [Enroll by ID](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-enrollassetsbyid?view=graph-rest-beta) | None | Enroll [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) resources of the same type in update management by Windows Autopatch. |
| [Unenroll from update management](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-unenrollassets?view=graph-rest-beta) | None | Unenroll [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) resources from update management by Windows Autopatch. |
| [Unenroll by ID](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-unenrollassetsbyid?view=graph-rest-beta) | None | Unenroll [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) resources of the same type from update management by Windows Autopatch. |
| [Add members](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-addmembers?view=graph-rest-beta) | None | Add members to an [updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta). |
| [Add members by ID](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-addmembersbyid?view=graph-rest-beta) | None | Add members of the same type to an [updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta). |
| [Remove members](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-removemembers?view=graph-rest-beta) | None | Remove members from an [updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta). |
| [Remove members by ID](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-removemembersbyid?view=graph-rest-beta) | None | Remove members of the same type from an [updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | An identifier for the asset. Key. Not nullable. Read-only. Returned by default. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.updatableAsset",
  "id": "String (identifier)"
}
```
