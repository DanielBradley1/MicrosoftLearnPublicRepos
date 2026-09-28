<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-endpoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# endpoint resource type

Namespace: microsoft.graph.callRecords

Represents an endpoint in a call. The endpoint could be a user's device, a meeting, an application/bot, etc. The [participantEndpoint](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participantendpoint?view=graph-rest-1.0) and [serviceEndpoint](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-serviceendpoint?view=graph-rest-1.0) types inherit from this type.

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
