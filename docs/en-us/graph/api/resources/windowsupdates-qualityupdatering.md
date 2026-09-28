<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatering?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# qualityUpdateRing resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an entity that governs the update deployment ring specifically for quality updates. An update deployment ring supports only devices and is used to phase the rollout strategy for quality updates.

Inherits from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta).

## Methods

For the list of supported methods, see [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the quality updates ring is created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| deferralInDays | Int32 | The quality update deferral period in days. The value must be between `0` and `30`. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| description | String | The quality update ring description. The maximum length is 1,500 characters. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| displayName | String | The quality update ring display name. The maximum length is 200 characters. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| excludedGroupAssignment | [microsoft.graph.windowsUpdates.excludedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-excludedgroupassignment?view=graph-rest-beta) | Governs the update deployment audience with excluded groups. Groups are logical containers of devices represented by Microsoft Entra groups. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| id | String | The unique identifier for the quality update ring. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| includedGroupAssignment | [microsoft.graph.windowsUpdates.includedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-includedgroupassignment?view=graph-rest-beta) | Governs the update deployment audience with included groups. Groups are logical containers of devices represented by Microsoft Entra groups. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| isHotpatchEnabled | Boolean | Identifies whether a hotpatch update is available. |
| isPaused | Boolean | Represents the pause action for the quality update ring policy. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time the quality updates ring was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.qualityUpdateRing",
  "createdDateTime": "String (timestamp)",
  "deferralInDays": "Int32",
  "description": "String",
  "displayName": "String",
  "excludedGroupAssignment": {"@odata.type": "microsoft.graph.windowsUpdates.excludedGroupAssignment"},
  "id": "String (identifier)",
  "includedGroupAssignment": {"@odata.type": "microsoft.graph.windowsUpdates.includedGroupAssignment"},
  "isHotpatchEnabled": "Boolean",
  "isPaused": "Boolean",
  "lastModifiedDateTime": "String (timestamp)"
}
```
