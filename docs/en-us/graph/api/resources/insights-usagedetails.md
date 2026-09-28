<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/insights-usagedetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# usageDetails resource type

Namespace: microsoft.graph

Complex type containing properties of [Used](https://learn.microsoft.com/en-us/graph/api/resources/insights-used?view=graph-rest-1.0) items. Information on when the resource was last accessed \(viewed\) or modified \(edited\) by the user.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| lastAccessedDateTime | DateTimeOffset | The date and time the resource was last accessed by the user. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time the resource was last modified by the user. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "lastAccessedDateTime": "DateTimeOffset",
  "lastModifiedDateTime": "DateTimeOffset"
}
```
