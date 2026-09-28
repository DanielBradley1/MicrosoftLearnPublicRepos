<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# cloudPcUserSettingAssignment resource type

Namespace: microsoft.graph

Represents a defined collection of user setting assignments.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when this assignment was created. The timestamp type represents the date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | Unique Identifier for the user setting assignment. If **target** is a user group, the ID has the following structure: `{policyID}\_{groupID}`. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| target | [cloudPcManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagementassignmenttarget?view=graph-rest-1.0) | The assignment target for the user setting. Currently, the only target supported for this user setting is a user group. For details, see [cloudPcManagementGroupAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagementgroupassignmenttarget?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcUserSettingAssignment",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "target": {"@odata.type": "microsoft.graph.cloudPcManagementAssignmentTarget"}
}
```
