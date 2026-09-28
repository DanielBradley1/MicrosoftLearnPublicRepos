<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/retentionsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-07 -->

# retentionSetting resource type

Namespace: microsoft.graph

Contains the details of the retention settings for a protection policy.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| interval | String | The frequency of the backup. |
| period | Duration | The period of time to retain the protected data for a single Microsoft 365 service. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.retentionSetting",
  "interval": "String",
  "period": "String (duration)"
}
```
