<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatering?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# driverUpdateRing resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a deployment ring that controls targeting, deferral, and pause settings for driver and firmware updates.

Inherits from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta).

## Methods

This resource is part of a polymorphic collection managed by the [ring resource](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) base type. Operations are performed through the base type endpoints.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the ring was created. Read-only. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| deferralInDays | Int32 | The number of days to defer the update offer. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| description | String | The ring description. The maximum length is 1,500 characters. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| displayName | String | The ring display name. The maximum length is 200 characters. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| excludedGroupAssignment | [microsoft.graph.windowsUpdates.excludedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-excludedgroupassignment?view=graph-rest-beta) | The Microsoft Entra groups whose devices are excluded from the ring. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| id | String | The unique identifier for the ring. Read-only. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| includedGroupAssignment | [microsoft.graph.windowsUpdates.includedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-includedgroupassignment?view=graph-rest-beta) | The Microsoft Entra groups whose devices are included in the ring. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| isPaused | Boolean | Indicates whether update offers for the ring are paused. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the ring was last modified. Read-only. Inherited from [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdateRing",
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
