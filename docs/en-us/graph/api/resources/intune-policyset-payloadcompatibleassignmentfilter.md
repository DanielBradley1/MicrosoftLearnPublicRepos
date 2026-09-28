<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadcompatibleassignmentfilter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# payloadCompatibleAssignmentFilter resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties used for Payload Compatible Assignment Filter.

Inherits from [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List payloadCompatibleAssignmentFilters](https://learn.microsoft.com/en-us/graph/api/intune-policyset-payloadcompatibleassignmentfilter-list?view=graph-rest-beta) | [payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadcompatibleassignmentfilter?view=graph-rest-beta) collection | List properties and relationships of the [payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadcompatibleassignmentfilter?view=graph-rest-beta) objects. |
| [Get payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/intune-policyset-payloadcompatibleassignmentfilter-get?view=graph-rest-beta) | [payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadcompatibleassignmentfilter?view=graph-rest-beta) | Read properties and relationships of the [payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadcompatibleassignmentfilter?view=graph-rest-beta) object. |
| [Create payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/intune-policyset-payloadcompatibleassignmentfilter-create?view=graph-rest-beta) | [payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadcompatibleassignmentfilter?view=graph-rest-beta) | Create a new [payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadcompatibleassignmentfilter?view=graph-rest-beta) object. |
| [Delete payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/intune-policyset-payloadcompatibleassignmentfilter-delete?view=graph-rest-beta) | None | Deletes a [payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadcompatibleassignmentfilter?view=graph-rest-beta). |
| [Update payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/intune-policyset-payloadcompatibleassignmentfilter-update?view=graph-rest-beta) | [payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadcompatibleassignmentfilter?view=graph-rest-beta) | Update the properties of a [payloadCompatibleAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadcompatibleassignmentfilter?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the Assignment Filter. Inherited from [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The creation time of the assignment filter. The value cannot be modified and is automatically populated during new assignment filter process. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Inherited from [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | Last modified time of the Assignment Filter. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z' Inherited from [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) |
| displayName | String | The name of the Assignment Filter. Inherited from [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) |
| description | String | Optional description of the Assignment Filter. Inherited from [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) |
| platform | [devicePlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceplatformtype?view=graph-rest-beta) | Indicates filter is applied to which flatform. Possible values are android,androidForWork,iOS,macOS,windowsPhone81,windows81AndLater,windows10AndLater,androidWorkProfile, unknown, androidAOSP, androidMobileApplicationManagement, iOSMobileApplicationManagement, windowsMobileApplicationManagement. Default filter will be applied to 'unknown'. Inherited from [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta). Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidAOSP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`, `windowsMobileApplicationManagement`. |
| rule | String | Rule definition of the assignment filter. Inherited from [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) |
| roleScopeTags | String collection | Indicates role scope tags assigned for the assignment filter. Inherited from [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) |
| payloads | [payloadByFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadbyfilter?view=graph-rest-beta) collection | Indicates associated assignments for a specific filter. Inherited from [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) |
| assignmentFilterManagementType | [assignmentFilterManagementType](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfiltermanagementtype?view=graph-rest-beta) | Indicates filter is applied to either 'devices' or 'apps' management type. Possible values are devices, apps. Default filter will be applied to 'devices' Inherited from [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta). Possible values are: `devices`, `apps`, `unknownFutureValue`. |
| payloadType | [assignmentFilterPayloadType](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfilterpayloadtype?view=graph-rest-beta) | PayloadType of the Assignment Filter. Possible values are: `notSet`, `enrollmentRestrictions`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.payloadCompatibleAssignmentFilter",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "description": "String",
  "platform": "String",
  "rule": "String",
  "roleScopeTags": [
    "String"
  ],
  "payloads": [
    {
      "@odata.type": "microsoft.graph.payloadByFilter",
      "payloadId": "String",
      "payloadType": "String",
      "groupId": "String",
      "assignmentFilterType": "String"
    }
  ],
  "assignmentFilterManagementType": "String",
  "payloadType": "String"
}
```
