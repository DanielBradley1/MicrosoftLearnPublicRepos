<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-exclusiongroupassignmenttarget?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# exclusionGroupAssignmentTarget resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents a group that should be excluded from an assignment.

Inherits from [groupAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-groupassignmenttarget?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceAndAppManagementAssignmentFilterId | String | The Id of the filter for the target assignment. Inherited from [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) |
| deviceAndAppManagementAssignmentFilterType | [deviceAndAppManagementAssignmentFilterType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmentfiltertype?view=graph-rest-beta) | The type of filter of the target assignment i.e. Exclude or Include. Inherited from [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta). Possible values are: `none`, `include`, `exclude`. |
| groupId | String | The group Id that is the target of the assignment. Inherited from [groupAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-groupassignmenttarget?view=graph-rest-beta) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.exclusionGroupAssignmentTarget",
  "deviceAndAppManagementAssignmentFilterId": "String",
  "deviceAndAppManagementAssignmentFilterType": "String",
  "groupId": "String"
}
```
