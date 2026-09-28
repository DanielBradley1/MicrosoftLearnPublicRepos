<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-traceroutehop?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# traceRouteHop resource type

Namespace: microsoft.graph.callRecords

Represents the network trace route hops collected for a [media stream](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-mediastream?view=graph-rest-1.0).

The `traceRouteHops` collection is not currently supported and returns an empty array.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hopCount | Int32 | The network path count of this hop that was used to compute the RTT. |
| ipAddress | String | IP address used for this hop in the network trace. |
| roundTripTime | Duration | The time from when the trace route packet was sent from the client to this hop and back to the client, denoted in [ISO 8601](https://www.iso.org/iso/iso8601) format. For example, 1 second is denoted as `PT1S`, where P is the duration designator, T is the time designator, and S is the second designator. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "hopCount": "Int32",
  "ipAddress": "String",
  "roundTripTime": "String (duration)"
}
```
