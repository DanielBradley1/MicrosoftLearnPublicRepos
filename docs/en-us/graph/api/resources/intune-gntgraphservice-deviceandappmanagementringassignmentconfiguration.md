<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# deviceAndAppManagementRingAssignmentConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A device and app management ring assignment configuration for deployment.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceAndAppManagementRingAssignmentConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration-list?view=graph-rest-beta) | [deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration?view=graph-rest-beta) objects. |
| [Get deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration-get?view=graph-rest-beta) | [deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration?view=graph-rest-beta) | Read properties and relationships of the [deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration?view=graph-rest-beta) object. |
| [Create deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration-create?view=graph-rest-beta) | [deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration?view=graph-rest-beta) | Create a new [deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration?view=graph-rest-beta) object. |
| [Delete deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration-delete?view=graph-rest-beta) | None | Deletes a [deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration?view=graph-rest-beta). |
| [Update deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration-update?view=graph-rest-beta) | [deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration?view=graph-rest-beta) | Update the properties of a [deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key for the resource. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The target assignment defined by the admin. |
| operation | [deviceAndAppManagementAssignmentOperationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignmentoperationtype?view=graph-rest-beta) | The target assignment operation. Possible values are: `add`, `unknownFutureValue`. |
| assignmentResults | [deviceAndAppManagementRingAssignmentResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentresult?view=graph-rest-beta) collection | Individual assignment status tracking for each payload |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementRingAssignmentConfiguration",
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
  },
  "operation": "String",
  "assignmentResults": [
    {
      "@odata.type": "microsoft.graph.deviceAndAppManagementRingAssignmentResult",
      "payloadId": "Guid",
      "status": "String",
      "message": "String"
    }
  ]
}
```
