<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamclasssettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamClassSettings resource type

Namespace: microsoft.graph

Represents class-specific properties of a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). Available only when the team represents a class.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| notifyGuardiansAboutAssignments | Boolean | If set to `true`, enables sending of weekly assignments digest emails to parents/guardians, provided the tenant admin has enabled the setting globally. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "notifyGuardiansAboutAssignments": true
}
```
