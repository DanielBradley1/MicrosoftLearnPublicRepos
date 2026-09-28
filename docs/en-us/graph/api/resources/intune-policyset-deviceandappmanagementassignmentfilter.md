<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceAndAppManagementAssignmentFilter resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties used for Assignment Filter.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceAndAppManagementAssignmentFilters](https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-list?view=graph-rest-beta) | [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) collection | List properties and relationships of the [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) objects. |
| [Get deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-get?view=graph-rest-beta) | [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) | Read properties and relationships of the [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) object. |
| [Create deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-create?view=graph-rest-beta) | [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) | Create a new [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) object. |
| [Delete deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-delete?view=graph-rest-beta) | None | Deletes a [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta). |
| [Update deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-update?view=graph-rest-beta) | [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) | Update the properties of a [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) object. |
| [validateFilter action](https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-validatefilter?view=graph-rest-beta) | [assignmentFilterValidationResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfiltervalidationresult?view=graph-rest-beta) |  |
| [enable action](https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-enable?view=graph-rest-beta) | None |  |
| [getState function](https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-getstate?view=graph-rest-beta) | [assignmentFilterState](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfilterstate?view=graph-rest-beta) |  |
| [getPlatformSupportedProperties function](https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-getplatformsupportedproperties?view=graph-rest-beta) | [assignmentFilterSupportedProperty](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfiltersupportedproperty?view=graph-rest-beta) collection |  |
| [getSupportedProperties function](https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-getsupportedproperties?view=graph-rest-beta) | [assignmentFilterSupportedProperty](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfiltersupportedproperty?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the Assignment Filter. |
| createdDateTime | DateTimeOffset | The creation time of the assignment filter. The value cannot be modified and is automatically populated during new assignment filter process. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. |
| lastModifiedDateTime | DateTimeOffset | Last modified time of the Assignment Filter. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z' |
| displayName | String | The name of the Assignment Filter. |
| description | String | Optional description of the Assignment Filter. |
| platform | [devicePlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceplatformtype?view=graph-rest-beta) | Indicates filter is applied to which flatform. Possible values are android,androidForWork,iOS,macOS,windowsPhone81,windows81AndLater,windows10AndLater,androidWorkProfile, unknown, androidAOSP, androidMobileApplicationManagement, iOSMobileApplicationManagement, windowsMobileApplicationManagement. Default filter will be applied to 'unknown'. Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidAOSP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`, `windowsMobileApplicationManagement`. |
| rule | String | Rule definition of the assignment filter. |
| roleScopeTags | String collection | Indicates role scope tags assigned for the assignment filter. |
| payloads | [payloadByFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadbyfilter?view=graph-rest-beta) collection | Indicates associated assignments for a specific filter. |
| assignmentFilterManagementType | [assignmentFilterManagementType](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfiltermanagementtype?view=graph-rest-beta) | Indicates filter is applied to either 'devices' or 'apps' management type. Possible values are devices, apps. Default filter will be applied to 'devices'. Possible values are: `devices`, `apps`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementAssignmentFilter",
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
  "assignmentFilterManagementType": "String"
}
```
