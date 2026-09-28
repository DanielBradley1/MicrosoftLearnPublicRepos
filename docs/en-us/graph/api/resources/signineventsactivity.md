<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signineventsactivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-01 -->

# signInEventsActivity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the summary of sign-in events for a specific day.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/auditlogroot-list-signineventssummary?view=graph-rest-beta) | [signInEventsActivity](https://learn.microsoft.com/en-us/graph/api/resources/signineventsactivity?view=graph-rest-beta) collection | Get a list of the signInEventsActivity objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityDateTime | DateTimeOffset | The aggregated day for which the summary applies to. This property always represents the entire day. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Supports `$filter` \(`gt`, `lt`\). |
| id | String | Identifier for the report. |
| signInCount | Int32 | The number of sign-in events that occurred for this day. Supports `$filter` \(`gt`, `lt`, `eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.signInEventsActivity",
  "id": "String (identifier)",
  "signInCount": "Integer",
  "activityDateTime": "String (timestamp)"
}
```
