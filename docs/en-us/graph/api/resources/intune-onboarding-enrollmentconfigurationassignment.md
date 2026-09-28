<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# enrollmentConfigurationAssignment resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Enrollment Configuration Assignment

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List enrollmentConfigurationAssignments](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-enrollmentconfigurationassignment-list?view=graph-rest-1.0) | [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0) collection | List properties and relationships of the [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0) objects. |
| [Get enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-enrollmentconfigurationassignment-get?view=graph-rest-1.0) | [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0) | Read properties and relationships of the [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0) object. |
| [Create enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-enrollmentconfigurationassignment-create?view=graph-rest-1.0) | [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0) | Create a new [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0) object. |
| [Delete enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-enrollmentconfigurationassignment-delete?view=graph-rest-1.0) | None | Deletes a [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0). |
| [Update enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-enrollmentconfigurationassignment-update?view=graph-rest-1.0) | [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0) | Update the properties of a [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the enrollment configuration assignment |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0) | Represents an assignment to managed devices in the tenant |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.enrollmentConfigurationAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "targetType": "String",
    "entraObjectId": "String"
  }
}
```
