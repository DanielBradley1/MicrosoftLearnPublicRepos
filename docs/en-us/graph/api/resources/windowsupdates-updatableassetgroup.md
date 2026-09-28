<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# updatableAssetGroup resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A group of [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) resources that can receive updates.

Members are of the [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) resource type. An **updatableAssetGroup** resource cannot be a member of another **updatableAssetGroup**.

Inherits from [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List updatableAssetGroup resources](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-list-updatableassets-updatableassetgroup?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta) objects and their properties. |
| [Create updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-post-updatableassets-updatableassetgroup?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta) | Create a new [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta) object. |
| [Get updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta) object. |
| [Delete updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-delete?view=graph-rest-beta) | None | Delete a [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta) object. |
| [Add members](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-addmembers?view=graph-rest-beta) | None | Add members to a [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta). |
| [Add members \(by ID\)](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-addmembers?view=graph-rest-beta) | None | Add members to a [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta). |
| [Remove members](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-removemembers?view=graph-rest-beta) | None | Remove members from a [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta). |
| [Remove members \(by ID\)](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-removemembers?view=graph-rest-beta) | None | Remove members from a [microsoft.graph.windowsUpdates.updatableAssetGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetgroup?view=graph-rest-beta). |
| [List members](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-list-members?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) collection | Get the [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) resources from the members navigation property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | An identifier for the group. Key. Not nullable. Read-only. Returned by default. Inherited from [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) collection | Members of the group. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.updatableAssetGroup",
  "id": "String (identifier)"
}
```
