<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/termsexpiration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# termsExpiration resource type

Namespace: microsoft.graph

Provides additional settings for the scheduled expiration of a terms of use [agreement](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| frequency | Duration | Represents the frequency at which the terms will expire, after its first expiration as set in **startDateTime**. The value is represented in ISO 8601 format for durations. For example, `PT1M` represents a time period of one month. |
| startDateTime | DateTimeOffset | The DateTime when the agreement is set to expire for all users. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
   "startDateTime": "2018-10-01T00:00:00.0000000Z",
   "frequency": "Duration"
}
```
