<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-serviceendpoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# serviceEndpoint resource type

Namespace: microsoft.graph.callRecords

Represents a service endpoint in a call. The endpoint represents a calling media server or other service entity. Inherits from [endpoint](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-endpoint?view=graph-rest-1.0) type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userAgent | [microsoft.graph.callRecords.userAgent](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-useragent?view=graph-rest-1.0) | User-agent reported by this endpoint. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "userAgent": {"@odata.type": "microsoft.graph.callRecords.userAgent"}
}
```
