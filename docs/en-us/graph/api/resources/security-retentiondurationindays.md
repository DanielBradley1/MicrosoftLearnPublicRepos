<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-retentiondurationindays?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# retentionDurationInDays resource type

Namespace: microsoft.graph.security

Represents the number of days an item will be retained before it can be deleted.

Inherits from [retentionDuration](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionduration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| days | Int32 | Specifies the time period in days for which an item with the applied retention label will be retained for. |

## Relationships

None.

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.retentionDurationInDays",
  "days": "Integer"
}
```
