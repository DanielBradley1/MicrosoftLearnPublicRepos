<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleenrollmentprofileassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# appleEnrollmentProfileAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

An assignment of an Apple profile.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List appleEnrollmentProfileAssignments](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleenrollmentprofileassignment-list?view=graph-rest-beta) | [appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleenrollmentprofileassignment?view=graph-rest-beta) collection | List properties and relationships of the [appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleenrollmentprofileassignment?view=graph-rest-beta) objects. |
| [Get appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleenrollmentprofileassignment-get?view=graph-rest-beta) | [appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleenrollmentprofileassignment?view=graph-rest-beta) | Read properties and relationships of the [appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleenrollmentprofileassignment?view=graph-rest-beta) object. |
| [Create appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleenrollmentprofileassignment-create?view=graph-rest-beta) | [appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleenrollmentprofileassignment?view=graph-rest-beta) | Create a new [appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleenrollmentprofileassignment?view=graph-rest-beta) object. |
| [Delete appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleenrollmentprofileassignment-delete?view=graph-rest-beta) | None | Deletes a [appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleenrollmentprofileassignment?view=graph-rest-beta). |
| [Update appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleenrollmentprofileassignment-update?view=graph-rest-beta) | [appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleenrollmentprofileassignment?view=graph-rest-beta) | Update the properties of a [appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleenrollmentprofileassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key of the assignment. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The assignment target for the Apple user initiated deployment profile. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.appleEnrollmentProfileAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String",
    "targetType": "String",
    "entraObjectId": "String"
  }
}
```
