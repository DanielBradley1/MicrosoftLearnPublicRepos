<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-scopetaggroupassignmenttarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# scopeTagGroupAssignmentTarget resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents a Scope Tag Assignment Target.

Inherits from [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| targetType | [scopeTagTargetType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-scopetagtargettype?view=graph-rest-1.0) | The Scope Tag Target Type to Apply the Assignment too. The possible values are: `none`, `user`, `device`, `unknownFutureValue`. |
| entraObjectId | String | The Entra Object Id that is the target of the assignment. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.scopeTagGroupAssignmentTarget",
  "targetType": "String",
  "entraObjectId": "String"
}
```
