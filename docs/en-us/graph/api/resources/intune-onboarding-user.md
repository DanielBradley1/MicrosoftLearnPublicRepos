<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-user?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# user resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List users](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-user-list?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-user?view=graph-rest-1.0) collection | List properties and relationships of the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-user?view=graph-rest-1.0) objects. |
| [Get user](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-user-get?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-user?view=graph-rest-1.0) | Read properties and relationships of the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-user?view=graph-rest-1.0) object. |
| [Create user](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-user-create?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-user?view=graph-rest-1.0) | Create a new [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-user?view=graph-rest-1.0) object. |
| [Delete user](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-user-delete?view=graph-rest-1.0) | None | Deletes a [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-user?view=graph-rest-1.0). |
| [Update user](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-user-update?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-user?view=graph-rest-1.0) | Update the properties of a [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-user?view=graph-rest-1.0) object. |
| [exportDeviceAndAppManagementData function](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-user-exportdeviceandappmanagementdata?view=graph-rest-1.0) | [deviceAndAppManagementData](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceandappmanagementdata?view=graph-rest-1.0) |  |
| [exportDeviceAndAppManagementData function](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-user-exportdeviceandappmanagementdata?view=graph-rest-1.0) | [deviceAndAppManagementData](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceandappmanagementdata?view=graph-rest-1.0) |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the user. |
| deviceEnrollmentLimit | Int32 | The limit on the maximum number of devices that the user is permitted to enroll. Allowed values are 5 or 1000. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.user",
  "id": "String (identifier)",
  "deviceEnrollmentLimit": 1024
}
```
