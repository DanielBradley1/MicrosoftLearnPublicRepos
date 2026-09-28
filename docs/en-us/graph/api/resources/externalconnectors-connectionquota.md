<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-connectionquota?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-21 -->

# connectionQuota resource type

Namespace: microsoft.graph.externalConnectors

Represents the [connection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-beta) quota that contains calculated information about the quota utilization of an external connection. It returns the allowed number of items that you can ingest into a connection by considering items ingested for the connection against the tenant-level quota for Microsoft 365 Copilot connectors \(formerly Microsoft Graph connectors\).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/externalconnectors-connectionquota-get?view=graph-rest-beta) | [connectionQuota](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-connectionquota?view=graph-rest-beta) | Retrieve the properties and relationships of a **connectionQuota**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| itemsRemaining | Int64 | The minimum of two values, one representing the *items remaining in the connection* and the other *remaining items at tenant-level*.  <br>The following equation represents the formula used to calculate the minimum number:  <br>min \({*﻿max capacity in the connection*} – {*﻿number of items in the connection*}, {*﻿tenant quota*} – {*﻿number of items indexed in all connections*}\).  <br>If the connection is not monetized, such as in a preview connector or preview content experience, then this property is simply the number of remaining items in the connection. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "itemsRemaining": "Int64"
}
```
