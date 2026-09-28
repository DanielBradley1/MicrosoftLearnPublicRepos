<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# deviceAndAppManagementAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents the assignment of a payload to a specific target, used to manage and track the details of payload assignments within the system.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceAndAppManagementAssignments](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementassignment-list?view=graph-rest-beta) | [deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignment?view=graph-rest-beta) collection | List properties and relationships of the [deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignment?view=graph-rest-beta) objects. |
| [Get deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementassignment-get?view=graph-rest-beta) | [deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignment?view=graph-rest-beta) | Read properties and relationships of the [deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignment?view=graph-rest-beta) object. |
| [Create deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementassignment-create?view=graph-rest-beta) | [deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignment?view=graph-rest-beta) | Create a new [deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignment?view=graph-rest-beta) object. |
| [Delete deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementassignment-delete?view=graph-rest-beta) | None | Deletes a [deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignment?view=graph-rest-beta). |
| [Update deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementassignment-update?view=graph-rest-beta) | [deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignment?view=graph-rest-beta) | Update the properties of a [deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignment?view=graph-rest-beta) object. |
| [assignments function](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementassignment-assignments?view=graph-rest-beta) | [deviceAndAppManagementAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignment?view=graph-rest-beta) collection |  |
| [reassignPayloadConflictsSetting action](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementassignment-reassignpayloadconflictssetting?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | A unique system generated identifier for the assignment. Read-Only. |
| payloadId | String | Indicates the identifier of a payload assigned to a target. Read-Only. |
| payloadDisplayName | String | Indicates the display name of a payload assigned to a target. Read-Only. |
| payloadDescription | String | Indicates the description of a payload assigned to a target. Read-Only. |
| assignmentFilterDisplayName | String | Indicates the display name of an assignment filter assigned to a target. Read-Only. |
| payloadTypeName | [deviceAndAppManagementPayloadType](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementpayloadtype?view=graph-rest-beta) | Indicates the type of payload being returned. For instance, SettingCatalog, SecurityBaseline, Antivirus and others. Read-Only. Possible values are: `unknown`, `settingsCatalog`, `securityBaseline`, `antivirus`, `diskEncryption`, `attackSurfaceReduction`, `firewall`, `endpointDetectionAndResponse`, `compliancePolicy`, `deviceRestrictions`, `unknownFutureValue`. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | Indicates the target for a payload. A payload can be directly assigned to a target or can be inherited. Read-Only. |
| assignmentLinkType | [deviceAndAppManagementAssignmentLinkType](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignmentlinktype?view=graph-rest-beta) | Default is unknown. Indicates if a payload is directly assigned to a target or is an inherited one. Read-Only. Possible values are: `unknown`, `direct`, `inherited`, `unknownFutureValue`. |
| managementArea | [deviceAndAppManagementArea](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementarea?view=graph-rest-beta) | Default is unknown. Indicates group of related payloads. These payloads can conflict when applied to a target settings. Conflict settings are used to prioritize payloads in such scenarios. Read-Only. Possible values are: `unknown`, `deviceConfiguration`, `app`, `compliance`, `unknownFutureValue`. |
| platformType | [devicePlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceplatformtype?view=graph-rest-beta) | Indicates the platform on which a payload is targeted to. Possible values are android, androidForWork, iOS, macOS, windowsPhone81, windows81AndLater, windows10AndLater, androidWorkProfile, androidAOSP, androidMobileApplicationManagement, iOSMobileApplicationManagement, windowsMobileApplicationManagement. Read-Only. Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidAOSP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`, `windowsMobileApplicationManagement`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementAssignment",
  "id": "String (identifier)",
  "payloadId": "String",
  "payloadDisplayName": "String",
  "payloadDescription": "String",
  "assignmentFilterDisplayName": "String",
  "payloadTypeName": "String",
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
  "assignmentLinkType": "String",
  "managementArea": "String",
  "platformType": "String"
}
```
