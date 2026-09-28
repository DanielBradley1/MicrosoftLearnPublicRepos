<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# hardwareConfigurationAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to assign a hardware configuration to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List hardwareConfigurationAssignments](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationassignment-list?view=graph-rest-beta) | [hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationassignment?view=graph-rest-beta) collection | List properties and relationships of the [hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationassignment?view=graph-rest-beta) objects. |
| [Get hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationassignment-get?view=graph-rest-beta) | [hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationassignment?view=graph-rest-beta) | Read properties and relationships of the [hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationassignment?view=graph-rest-beta) object. |
| [Create hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationassignment-create?view=graph-rest-beta) | [hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationassignment?view=graph-rest-beta) | Create a new [hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationassignment?view=graph-rest-beta) object. |
| [Delete hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationassignment-delete?view=graph-rest-beta) | None | Deletes a [hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationassignment?view=graph-rest-beta). |
| [Update hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationassignment-update?view=graph-rest-beta) | [hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationassignment?view=graph-rest-beta) | Update the properties of a [hardwareConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the hardware configuration group assignment entity. This property is read-only. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The Id of the Azure Active Directory group we are targeting the configuration to. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.hardwareConfigurationAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.organizationalUnitAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String",
    "organizationalUnitId": "String",
    "assignmentConflictSetting": {
      "@odata.type": "microsoft.graph.organizationalUnitAssignmentConflictSetting",
      "assignmentOverride": "String",
      "versionNumber": 1024
    }
  }
}
```
