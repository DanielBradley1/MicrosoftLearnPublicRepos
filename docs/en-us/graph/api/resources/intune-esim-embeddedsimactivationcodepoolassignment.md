<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# embeddedSIMActivationCodePoolAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The embedded SIM activation code pool assignment entity assigns a specific embeddedSIMActivationCodePool to an AAD device group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List embeddedSIMActivationCodePoolAssignments](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimactivationcodepoolassignment-list?view=graph-rest-beta) | [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta) collection | List properties and relationships of the [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta) objects. |
| [Get embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimactivationcodepoolassignment-get?view=graph-rest-beta) | [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta) | Read properties and relationships of the [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta) object. |
| [Create embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimactivationcodepoolassignment-create?view=graph-rest-beta) | [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta) | Create a new [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta) object. |
| [Delete embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimactivationcodepoolassignment-delete?view=graph-rest-beta) | None | Deletes a [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta). |
| [Update embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimactivationcodepoolassignment-update?view=graph-rest-beta) | [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta) | Update the properties of a [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the embedded SIM activation code pool assignment. System generated value assigned when created. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The type of groups targeted by the embedded SIM activation code pool. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.embeddedSIMActivationCodePoolAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.allLicensedUsersAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String"
  }
}
```
