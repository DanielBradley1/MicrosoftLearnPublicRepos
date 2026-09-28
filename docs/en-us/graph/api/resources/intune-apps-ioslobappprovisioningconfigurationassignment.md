<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosLobAppProvisioningConfigurationAssignment resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties used for Group Assignment of an iOS LOB App Provisioning and Configuration.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosLobAppProvisioningConfigurationAssignments](https://learn.microsoft.com/en-us/graph/api/intune-apps-ioslobappprovisioningconfigurationassignment-list?view=graph-rest-1.0) | [iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment?view=graph-rest-1.0) collection | List properties and relationships of the [iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment?view=graph-rest-1.0) objects. |
| [Get iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-ioslobappprovisioningconfigurationassignment-get?view=graph-rest-1.0) | [iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment?view=graph-rest-1.0) | Read properties and relationships of the [iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment?view=graph-rest-1.0) object. |
| [Create iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-ioslobappprovisioningconfigurationassignment-create?view=graph-rest-1.0) | [iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment?view=graph-rest-1.0) | Create a new [iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment?view=graph-rest-1.0) object. |
| [Delete iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-ioslobappprovisioningconfigurationassignment-delete?view=graph-rest-1.0) | None | Deletes a [iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment?view=graph-rest-1.0). |
| [Update iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-ioslobappprovisioningconfigurationassignment-update?view=graph-rest-1.0) | [iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment?view=graph-rest-1.0) | Update the properties of a [iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0) | The target group assignment defined by the admin. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosLobAppProvisioningConfigurationAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.deviceAndAppManagementAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String"
  }
}
```
