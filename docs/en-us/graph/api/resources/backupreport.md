<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/backupreport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# backupReport resource type

Namespace: microsoft.graph

Represents an abstract backup report. This resource can't be instantiated directly.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get statistics by policy](https://learn.microsoft.com/en-us/graph/api/backupreport-getstatisticsbypolicy?view=graph-rest-1.0) | [backupPolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/backuppolicyreport?view=graph-rest-1.0) | Get the statistics that correspond to the specified policy ID of a [backupPolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/backuppolicyreport?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the backup report. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.backupReport",
  "id": "String (identifier)"
}
```
