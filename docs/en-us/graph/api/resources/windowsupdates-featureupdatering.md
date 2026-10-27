<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-featureupdatering?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# featureUpdateRing resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an entity that governs the update deployment ring specifically for feature updates. An update deployment ring supports only devices and is used to phase the rollout strategy for feature updates.

The ring's offer-window settings control how gradually the update reaches devices: **offerIntervalInDays** determines how often a new subset of devices is offered the update, and **offerDurationInDays** sets the total length of that rollout window. Set **offerIntervalInDays** to `0` to offer the update to all devices at once.

Inherits from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta).

## Methods

This resource is part of a polymorphic collection managed by the [ring resource](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) base type. Operations are performed through the base type endpoints.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the feature updates ring is created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| deferralInDays | Int32 | The feature update deferral period in days. The value must be between `0` and `30`. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| description | String | The feature update ring description. The maximum length is 1,500 characters. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| displayName | String | The feature update ring display name. The maximum length is 200 characters. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| excludedGroupAssignment | [microsoft.graph.windowsUpdates.excludedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-excludedgroupassignment?view=graph-rest-beta) | Governs the update deployment audience with excluded groups. Groups are logical containers of devices represented by Microsoft Entra groups. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| id | String | The unique identifier for the feature update ring. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| includedGroupAssignment | [microsoft.graph.windowsUpdates.includedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-includedgroupassignment?view=graph-rest-beta) | Governs the update deployment audience with included groups. Groups are logical containers of devices represented by Microsoft Entra groups. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| isOfferOptional | Boolean | Indicates whether the feature update is offered to end users as optional rather than required. Default is `false`. |
| isPaused | Boolean | Represents the pause action for the feature update ring policy. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time the feature updates ring was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| offerDurationInDays | Int32 | The total length of the gradual-rollout window, in days, from when the update is first offered to when the rollout completes. The minimum is `1`. Only used when **offerIntervalInDays** is `1` or greater; ignored when **offerIntervalInDays** is `0`. Default is `1`. |
| offerIntervalInDays | Int32 | How often, in days, a new subset of devices is offered the update. Accepted range is `0` to `30`. Set to `0` to offer the update to all devices at once. When the value is `1` or greater, the rollout advances one subset at each interval until every device has been offered the update. Must be less than or equal to **offerDurationInDays**. Default is `0`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.featureUpdateRing",
  "createdDateTime": "String (timestamp)",
  "deferralInDays": "Int32",
  "description": "String",
  "displayName": "String",
  "excludedGroupAssignment": {"@odata.type": "microsoft.graph.windowsUpdates.excludedGroupAssignment"},
  "id": "String (identifier)",
  "includedGroupAssignment": {"@odata.type": "microsoft.graph.windowsUpdates.includedGroupAssignment"},
  "isOfferOptional": "Boolean",
  "isPaused": "Boolean",
  "lastModifiedDateTime": "String (timestamp)",
  "offerDurationInDays": "Int32",
  "offerIntervalInDays": "Int32"
}
```
