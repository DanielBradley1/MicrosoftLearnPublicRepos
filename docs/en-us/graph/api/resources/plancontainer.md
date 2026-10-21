<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plancontainer?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# planContainer resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **container** property of the [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) resource uses this type.

Identifies the container - a group, a Teams channel, or a user - that a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) belongs to. `containerType` and `containerId` are both required when filtering the top-level /planner/plans\_v2 collection.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| containerId | String | ID of the container \(group ID, user ID, or Teams channel ID\). |
| containerType | plannerContainerType | Type of the container that owns the plan. The possible values are: `group`, `unknownFutureValue`, `roster`, `project`, `driveItem`, `user`, `teamsChannel`, `onlineMeeting`, `plannerTask`, `officeDocument`, `meeting`, `dataverseProject`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `roster` , `project` , `driveItem` , `user` , `teamsChannel` , `onlineMeeting` , `plannerTask` , `officeDocument` , `meeting` , `dataverseProject`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.planContainer",
  "containerId": "String",
  "containerType": "String"
}
```
