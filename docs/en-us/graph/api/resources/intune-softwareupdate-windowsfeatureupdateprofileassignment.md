<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsFeatureUpdateProfileAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This entity contains the properties used to assign a windows feature update profile to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsFeatureUpdateProfileAssignments](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdateprofileassignment-list?view=graph-rest-beta) | [windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment?view=graph-rest-beta) collection | List properties and relationships of the [windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment?view=graph-rest-beta) objects. |
| [Get windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdateprofileassignment-get?view=graph-rest-beta) | [windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment?view=graph-rest-beta) | Read properties and relationships of the [windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment?view=graph-rest-beta) object. |
| [Create windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdateprofileassignment-create?view=graph-rest-beta) | [windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment?view=graph-rest-beta) | Create a new [windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment?view=graph-rest-beta) object. |
| [Delete windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdateprofileassignment-delete?view=graph-rest-beta) | None | Deletes a [windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment?view=graph-rest-beta). |
| [Update windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdateprofileassignment-update?view=graph-rest-beta) | [windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment?view=graph-rest-beta) | Update the properties of a [windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The Identifier of the entity |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The assignment target that the feature update profile is assigned to. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsFeatureUpdateProfileAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.deviceAndAppManagementAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String"
  }
}
```
