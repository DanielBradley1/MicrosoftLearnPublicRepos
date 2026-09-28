<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/projectrome-historyitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# activityHistoryItem resource type

Namespace: microsoft.graph

Represents a history item for an [activity](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-activity?view=graph-rest-1.0) in an app. User activities represent a single destination within your app; for example, a TV show, a document, or a current campaign in a video game. When a user engages with that activity, the engagement is captured as a history item that indicates the start and end time for that activity. As the user re-engages with that activity over time, multiple history items are recorded for a single user activity.

When an app creates a session, a **activityHistoryItem** object should be added to the **activity** object to reflect the period of user engagement. Each time a user re-engages with an activity, a new **activityHistoryItem** is added to the activity to accrue user engagement.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create or replace a history item](https://learn.microsoft.com/en-us/graph/api/projectrome-put-historyitem?view=graph-rest-1.0) | [activityHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-historyitem?view=graph-rest-1.0) | Create or replace an existing **activityHistoryItem** for that activity \(upsert\). The ID needs to be a GUID. |
| [Delete a history item](https://learn.microsoft.com/en-us/graph/api/projectrome-delete-historyitem?view=graph-rest-1.0) | No Content | Delete the specified **activityHistoryItem** for that activity. |

## Properties

| Name | Type | Description |
| :--- | :--- | :--- |
| activeDurationSeconds | int | Optional. The duration of active user engagement. if not supplied, this is calculated from the **startedDateTime** and **lastActiveDateTime**. |
| createdDateTime | DateTimeOffset | Set by the server. DateTime in UTC when the object was created on the server. |
| expirationDateTime | DateTimeOffset | Optional. UTC DateTime when the **activityHistoryItem** will undergo hard-delete. Can be set by the client. |
| id | String | Required. Client-set GUID for the **activityHistoryItem** object. |
| lastActiveDateTime | DateTimeOffset | Optional. UTC DateTime when the **activityHistoryItem** \(activity session\) was last understood as active or finished - if null, **activityHistoryItem** status should be Ongoing. |
| lastModifiedDateTime | DateTimeOffset | Set by the server. DateTime in UTC when the object was modified on the server. |
| startedDateTime | DateTimeOffset | Required. UTC DateTime when the **activityHistoryItem** \(activity session\) was started. Required for timeline history. |
| status | status | Set by the server. A status code used to identify valid objects. Values: active, updated, deleted, ignored. |
| userTimezone | String | Optional. The timezone in which the user's device used to generate the activity was located at activity creation time. Values supplied as Olson IDs in order to support cross-platform representation. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activity | [userActivity](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-activity?view=graph-rest-1.0) | Optional. NavigationProperty/Containment; navigation property to the associated activity. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "activeDurationSeconds":"int",
    "createdDateTime": "DateTimeOffset",
    "expirationDateTime": "DateTimeOffset",
    "id": "String",
    "lastActiveDateTime": "DateTimeOffset",
    "lastModifiedDateTime": "DateTimeOffset",
    "startedDateTime": "DateTimeOffset",
    "status": "String",
    "userTimezone": "String"
}
```
