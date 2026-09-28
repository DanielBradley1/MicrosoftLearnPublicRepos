<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecategory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceCategory resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device categories provides a way to organize your devices. Using device categories, company administrators can define their own categories that make sense to their company. These categories can then be applied to a device in the Intune Azure console or selected by a user during device enrollment. You can filter reports and create dynamic Azure Active Directory device groups based on device categories.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceCategories](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicecategory-list?view=graph-rest-1.0) | [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecategory?view=graph-rest-1.0) collection | List properties and relationships of the [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecategory?view=graph-rest-1.0) objects. |
| [Get deviceCategory](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicecategory-get?view=graph-rest-1.0) | [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecategory?view=graph-rest-1.0) | Read properties and relationships of the [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecategory?view=graph-rest-1.0) object. |
| [Create deviceCategory](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicecategory-create?view=graph-rest-1.0) | [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecategory?view=graph-rest-1.0) | Create a new [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecategory?view=graph-rest-1.0) object. |
| [Delete deviceCategory](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicecategory-delete?view=graph-rest-1.0) | None | Deletes a [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecategory?view=graph-rest-1.0). |
| [Update deviceCategory](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicecategory-update?view=graph-rest-1.0) | [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecategory?view=graph-rest-1.0) | Update the properties of a [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecategory?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the device category. Read-only. |
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
