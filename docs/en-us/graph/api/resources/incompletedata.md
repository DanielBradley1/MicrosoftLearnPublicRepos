<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/incompletedata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# incompleteData resource type

Namespace: microsoft.graph

The **incompleteData** facet indicates that a resource was generated with incomplete data. The properties within might provide information about why the data is incomplete.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| missingDataBeforeDateTime | DateTimeOffset | The service does not have source data before the specified time. |
| wasThrottled | Boolean | Some data was not recorded due to excessive activity. |

## JSON representation

```json
{
  "missingDataBeforeDateTime": "String (timestamp)",
  "wasThrottled": false
}
```
