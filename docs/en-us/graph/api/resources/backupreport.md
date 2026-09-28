<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/backupreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# backupReport resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract backup report. This resource can't be instantiated directly.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get statistics by policy](https://learn.microsoft.com/en-us/graph/api/backupreport-getstatisticsbypolicy?view=graph-rest-beta) | [backupPolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/backuppolicyreport?view=graph-rest-beta) | Get the statistics that correspond to the specified policy ID of a [backupPolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/backuppolicyreport?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the backup report. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

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
