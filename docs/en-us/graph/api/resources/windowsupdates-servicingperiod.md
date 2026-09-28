<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-servicingperiod?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# servicingPeriod resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information about a servicing period related to a product edition. Each edition of a particular product has one or more servicing periods.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTimeOffset | The date and time when the servicing period ends. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| name | String | The name of the servicing period. For example, `Modern Lifecycle`. |
| startDateTime | DateTimeOffset | The start date and time of the servicing period. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.servicingPeriod",
  "endDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "name": "String",
  "startDateTime": "String (timestamp)"
}
```
