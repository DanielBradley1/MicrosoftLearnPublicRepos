<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-useragent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# userAgent resource type

Namespace: microsoft.graph.callRecords

Represents the user agent of an endpoint in a call. The [clientUserAgent](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-clientuseragent?view=graph-rest-1.0) and [serviceUserAgent](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-serviceuseragent?view=graph-rest-1.0) types inherit from this type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationVersion | String | Identifies the version of application software used by this endpoint. |
| headerValue | String | User-agent header value reported by this endpoint. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "applicationVersion": "String",
  "headerValue": "String"
}
```
