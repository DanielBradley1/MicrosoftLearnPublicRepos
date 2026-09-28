<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementIntentAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Intent assignment entity

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementIntentAssignments](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentassignment-list?view=graph-rest-beta) | [deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment?view=graph-rest-beta) objects. |
| [Get deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentassignment-get?view=graph-rest-beta) | [deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment?view=graph-rest-beta) object. |
| [Create deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentassignment-create?view=graph-rest-beta) | [deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment?view=graph-rest-beta) | Create a new [deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment?view=graph-rest-beta) object. |
| [Delete deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentassignment-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment?view=graph-rest-beta). |
| [Update deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentassignment-update?view=graph-rest-beta) | [deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment?view=graph-rest-beta) | Update the properties of a [deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The assignment ID |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The assignment target |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementIntentAssignment",
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
