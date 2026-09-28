<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-23 -->

# azureADDevice resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a device in Microsoft Entra ID that is registered with Windows Autopatch.

A Microsoft Entra device is automatically created through one of the following methods:

- [updatableAsset: enrollAssets](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-enrollassets?view=graph-rest-beta)
- [updatableAsset: enrollAssetsById](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-enrollassetsbyid?view=graph-rest-beta)
- [deploymentAudience: updateAudience](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-updateaudience?view=graph-rest-beta)
- [deploymentAudience: updateAudienceById](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-updateaudiencebyid?view=graph-rest-beta)
- [updatableAssetGroup: addMembers](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-addmembers?view=graph-rest-beta)
- [updatableAssetGroup: addMembersById](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableassetgroup-addmembersbyid?view=graph-rest-beta)

Inherits from [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List Microsoft Entra devices](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-list-updatableassets-azureaddevice?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) collection | Get a list of the [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) objects and their properties. |
| [Get Microsoft Entra device](https://learn.microsoft.com/en-us/graph/api/windowsupdates-azureaddevice-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) | Read the properties and relationships of an [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) object. |
| [Delete Microsoft Entra device](https://learn.microsoft.com/en-us/graph/api/windowsupdates-azureaddevice-delete?view=graph-rest-beta) | None | Delete an [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) object. |
| [Enroll in update management](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-enrollassets?view=graph-rest-beta) | None | Enroll [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) resources in update management by Windows Autopatch. |
| [Enroll by ID](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-enrollassetsbyid?view=graph-rest-beta) | None | Enroll [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) resources of the same type in update management by Windows Autopatch. |
| [Unenroll from update management](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-unenrollassets?view=graph-rest-beta) | None | Unenroll [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) resources from update management by Windows Autopatch. |
| [Unenroll by ID](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatableasset-unenrollassetsbyid?view=graph-rest-beta) | None | Unenroll [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) resources of the same type from update management by Windows Autopatch. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enrollment | [microsoft.graph.windowsUpdates.updateManagementEnrollment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatemanagementenrollment?view=graph-rest-beta) | Specifies the update management enrollment for the device. Read-only. Returned by default. |
| errors | [microsoft.graph.windowsUpdates.updatableAssetError](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasseterror?view=graph-rest-beta) collection | Specifies any errors that prevent the device from being enrolled in update management or receiving deployed content. Read-only. Returned by default. |
| id | String | An identifier for the device. Key. Not nullable. Read-only. Returned by default. Inherited from [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.azureADDevice",
  "id": "String (identifier)",
  "errors": [
    {
      "@odata.type": "microsoft.graph.windowsUpdates.azureADDeviceRegistrationError"
    }
  ],
  "enrollment": {"@odata.type": "#microsoft.graph.windowsUpdates.updateManagementEnrollment"}
}
```
