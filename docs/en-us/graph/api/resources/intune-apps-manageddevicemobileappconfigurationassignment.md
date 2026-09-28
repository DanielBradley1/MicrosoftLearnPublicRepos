<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedDeviceMobileAppConfigurationAssignment resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains the properties used to assign an MDM app configuration to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedDeviceMobileAppConfigurationAssignments](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationassignment-list?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0) collection | List properties and relationships of the [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0) objects. |
| [Get managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationassignment-get?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0) | Read properties and relationships of the [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0) object. |
| [Create managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationassignment-create?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0) | Create a new [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0) object. |
| [Delete managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationassignment-delete?view=graph-rest-1.0) | None | Deletes a [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0). |
| [Update managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationassignment-update?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0) | Update the properties of a [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the entity. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0) | Assignment target that the T&C policy is assigned to. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDeviceMobileAppConfigurationAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.allLicensedUsersAssignmentTarget"
  }
}
```
