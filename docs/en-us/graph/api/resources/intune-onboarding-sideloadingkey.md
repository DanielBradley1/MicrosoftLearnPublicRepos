<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# sideLoadingKey resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

SideLoadingKey entity is required for Windows 8 and 8.1 devices to intall Line Of Business Apps for a tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List sideLoadingKeies](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-sideloadingkey-list?view=graph-rest-beta) | [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey?view=graph-rest-beta) collection | List properties and relationships of the [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey?view=graph-rest-beta) objects. |
| [Get sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-sideloadingkey-get?view=graph-rest-beta) | [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey?view=graph-rest-beta) | Read properties and relationships of the [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey?view=graph-rest-beta) object. |
| [Create sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-sideloadingkey-create?view=graph-rest-beta) | [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey?view=graph-rest-beta) | Create a new [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey?view=graph-rest-beta) object. |
| [Delete sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-sideloadingkey-delete?view=graph-rest-beta) | None | Deletes a [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey?view=graph-rest-beta). |
| [Update sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-sideloadingkey-update?view=graph-rest-beta) | [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey?view=graph-rest-beta) | Update the properties of a [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Side Loading Key Unique Id. |
| value | String | Side Loading Key Value, it is 5x5 value, seperated by hiphens. |
| displayName | String | Side Loading Key Name displayed to the ITPro Admins. |
| description | String | Side Loading Key description displayed to the ITPro Admins.. |
| totalActivation | Int32 | Side Loading Key Total Activation displayed to the ITPro Admins. |
| lastUpdatedDateTime | String | Side Loading Key Last Updated Date displayed to the ITPro Admins. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.sideLoadingKey",
  "id": "String (identifier)",
  "value": "String",
  "displayName": "String",
  "description": "String",
  "totalActivation": 1024,
  "lastUpdatedDateTime": "String"
}
```
