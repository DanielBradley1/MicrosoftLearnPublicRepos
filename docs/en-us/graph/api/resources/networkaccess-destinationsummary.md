<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-destinationsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# destinationSummary resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A summary for device destinations.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| count | Int32 | The number of the destinationSummary objects, aggregated by Global Secure Access service. |
| destination | String | The IP address or FQDN of the destination. |
| trafficType | microsoft.graph.networkaccess.trafficType | The traffic classification. The allowed values are `internet`, `private`, `microsoft365`, `all`, and `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.destinationSummary",
  "destination": "String",
  "count": "Integer",
  "trafficType": "String"
}
```
