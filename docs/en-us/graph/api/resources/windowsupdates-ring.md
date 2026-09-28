<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# ring resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that governs the update deployment ring. An update deployment ring supports only devices and is used to phase a rollout strategy for Windows updates.

Base type of [qualityUpdateRing](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatering?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-list-rings?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) collection | Get a list of the [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-post-rings?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) | Create a new [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/windowsupdates-ring-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) | Read the properties and relationships of [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/windowsupdates-ring-update?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) | Update the properties of a [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/windowsupdates-ring-delete?view=graph-rest-beta) | None | Delete a [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the ring is created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only |
| deferralInDays | Int32 | The quality update deferral period in days. The value must be between `0` and `30`. Optional. |
| description | String | The ring description. The maximum length is 1,500 characters. Required |
| displayName | String | The ring display name. The maximum length is 200 characters. Required. |
| excludedGroupAssignment | [microsoft.graph.windowsUpdates.excludedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-excludedgroupassignment?view=graph-rest-beta) | Governs the update deployment audience with excluded groups. Groups are logical containers of devices represented by Microsoft Entra groups. |
| id | String | The unique identifier for the **ring** object. |
| includedGroupAssignment | [microsoft.graph.windowsUpdates.includedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-includedgroupassignment?view=graph-rest-beta) | Governs the update deployment audience with included groups. Groups are logical containers of devices represented by Microsoft Entra groups. |
| isPaused | Boolean | The pause action for the quality update ring policy. Required. |
| lastModifiedDateTime | DateTimeOffset | The date and time whenthe ring was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.ring",
  "createdDateTime": "String (timestamp)",
  "deferralInDays": "Int32",
  "description": "String",
  "displayName": "String",
  "excludedGroupAssignment": {"@odata.type": "microsoft.graph.windowsUpdates.excludedGroupAssignment"},
  "id": "String (identifier)",
  "includedGroupAssignment": {"@odata.type": "microsoft.graph.windowsUpdates.includedGroupAssignment"},
  "isPaused": "Boolean",
  "lastModifiedDateTime": "String (timestamp)"
}
```
