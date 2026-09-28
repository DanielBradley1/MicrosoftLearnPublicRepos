<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceCategory resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device categories provide a way to organize your devices. Using device categories, company administrators can define unique categories that make sense to their company. These categories can then be applied to a device in the Intune Azure console or selected by a user during device enrollment. You can filter reports and create dynamic Azure Active Directory device groups based on device categories.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceCategories](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicecategory-list?view=graph-rest-beta) | [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta) collection | List properties and relationships of the [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta) objects. |
| [Get deviceCategory](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicecategory-get?view=graph-rest-beta) | [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta) | Read properties and relationships of the [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta) object. |
| [Create deviceCategory](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicecategory-create?view=graph-rest-beta) | [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta) | Create a new [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta) object. |
| [Delete deviceCategory](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicecategory-delete?view=graph-rest-beta) | None | Deletes a [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta). |
| [Update deviceCategory](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicecategory-update?view=graph-rest-beta) | [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta) | Update the properties of a [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the device category. Read-only. |
| **Onboarding** |  |  |
| displayName | String | Display name for the device category. |
| description | String | Optional description for the device category. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceCategory",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String"
}
```
