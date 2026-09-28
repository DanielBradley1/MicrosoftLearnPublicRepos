<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printershareviewpoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# printerShareViewpoint resource type

Namespace: microsoft.graph

Represents user-specific data for a printer share as viewed by the signed-in user.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastUsedDateTime | DateTimeOffset | Date and time when the printer was last used by the signed-in user. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printerShareViewpoint",
  "lastUsedDateTime": "String (timestamp)"
}
```
