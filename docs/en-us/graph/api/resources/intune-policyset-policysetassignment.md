<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# policySetAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties used for PolicySet Assignment.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List policySetAssignments](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policysetassignment-list?view=graph-rest-beta) | [policySetAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment?view=graph-rest-beta) collection | List properties and relationships of the [policySetAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment?view=graph-rest-beta) objects. |
| [Get policySetAssignment](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policysetassignment-get?view=graph-rest-beta) | [policySetAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment?view=graph-rest-beta) | Read properties and relationships of the [policySetAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment?view=graph-rest-beta) object. |
| [Create policySetAssignment](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policysetassignment-create?view=graph-rest-beta) | [policySetAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment?view=graph-rest-beta) | Create a new [policySetAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment?view=graph-rest-beta) object. |
| [Delete policySetAssignment](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policysetassignment-delete?view=graph-rest-beta) | None | Deletes a [policySetAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment?view=graph-rest-beta). |
| [Update policySetAssignment](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policysetassignment-update?view=graph-rest-beta) | [policySetAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment?view=graph-rest-beta) | Update the properties of a [policySetAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the PolicySetAssignment. |
| lastModifiedDateTime | DateTimeOffset | Last modified time of the PolicySetAssignment. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The target group of PolicySetAssignment |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.policySetAssignment",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String",
    "targetType": "String",
    "entraObjectId": "String"
  }
}
```
