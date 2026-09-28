<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connectionsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# connectionSummary resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides a summary of connections in Global Secure Access grouped by traffic type, for both Internet Access and Private Access traffic.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| totalCount | Int32 | Total number of connections for the specified traffic type. |
| trafficType | microsoft.graph.networkaccess.trafficType | The type of network traffic these connections represent. The possible values are: `internet`, `private`, `microsoft365`, `all`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.connectionSummary",
  "trafficType": "String",
  "totalCount": "Integer"
}
```
