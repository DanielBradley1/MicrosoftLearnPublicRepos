<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# mobileAppAssignment resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties used for Group Assignment of a Mobile App.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileAppAssignments](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappassignment-list?view=graph-rest-1.0) | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) collection | List properties and relationships of the [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) objects. |
| [Get mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappassignment-get?view=graph-rest-1.0) | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) | Read properties and relationships of the [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) object. |
| [Create mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappassignment-create?view=graph-rest-1.0) | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) | Create a new [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) object. |
| [Delete mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappassignment-delete?view=graph-rest-1.0) | None | Deletes a [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0). |
| [Update mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappassignment-update?view=graph-rest-1.0) | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) | Update the properties of a [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. |
| intent | [installIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-installintent?view=graph-rest-1.0) | The install intent defined by the admin. The possible values are: `available`, `required`, `uninstall`, `availableWithoutEnrollment`. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0) | The target group assignment defined by the admin. |
| settings | [mobileAppAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignmentsettings?view=graph-rest-1.0) | The settings for target assignment defined by the admin. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppAssignment",
  "id": "String (identifier)",
  "intent": "String",
  "target": {
    "@odata.type": "microsoft.graph.allLicensedUsersAssignmentTarget"
  },
  "settings": {
    "@odata.type": "microsoft.graph.windowsUniversalAppXAppAssignmentSettings",
    "useDeviceContext": true
  }
}
```
