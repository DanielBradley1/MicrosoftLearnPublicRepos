<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementResourceAccessProfileAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that describes tenant level settings for derived credentials

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementResourceAccessProfileAssignments](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementresourceaccessprofileassignment-list?view=graph-rest-beta) | [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) objects. |
| [Get deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementresourceaccessprofileassignment-get?view=graph-rest-beta) | [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) object. |
| [Create deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementresourceaccessprofileassignment-create?view=graph-rest-beta) | [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) | Create a new [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) object. |
| [Delete deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementresourceaccessprofileassignment-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta). |
| [Update deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementresourceaccessprofileassignment-update?view=graph-rest-beta) | [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) | Update the properties of a [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the Assignments |
| intent | [deviceManagementResourceAccessProfileIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileintent?view=graph-rest-beta) | The assignment intent for the resource access profile. Possible values are: `apply`, `remove`. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The assignment target for the resource access profile. |
| sourceId | String | The identifier of the source of the assignment. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementResourceAccessProfileAssignment",
  "id": "String (identifier)",
  "intent": "String",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String",
    "targetType": "String",
    "entraObjectId": "String"
  },
  "sourceId": "String"
}
```
