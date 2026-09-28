<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-media?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-08 -->

# media resource type

Namespace: microsoft.graph.callRecords

Represents the media \(for example, audio, video, and video-based screen-sharing\) used in a call.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| calleeDevice | [microsoft.graph.callRecords.deviceInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-deviceinfo?view=graph-rest-1.0) | Device information associated with the callee endpoint of this media. |
| calleeNetwork | [microsoft.graph.callRecords.networkInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-networkinfo?view=graph-rest-1.0) | Network information associated with the callee endpoint of this media. |
| callerDevice | [microsoft.graph.callRecords.deviceInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-deviceinfo?view=graph-rest-1.0) | Device information associated with the caller endpoint of this media. |
| callerNetwork | [microsoft.graph.callRecords.networkInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-networkinfo?view=graph-rest-1.0) | Network information associated with the caller endpoint of this media. |
| label | String | How the media was identified during media negotiation stage. |
| streams | [microsoft.graph.callRecords.mediaStream](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-mediastream?view=graph-rest-1.0) collection | Network streams associated with this media. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "calleeDevice": {"@odata.type": "microsoft.graph.callRecords.deviceInfo"},
  "calleeNetwork": {"@odata.type": "microsoft.graph.callRecords.networkInfo"},
  "callerDevice": {"@odata.type": "microsoft.graph.callRecords.deviceInfo"},
  "callerNetwork": {"@odata.type": "microsoft.graph.callRecords.networkInfo"},
  "label": "String",
  "streams": [{"@odata.type": "microsoft.graph.callRecords.mediaStream"}]
}
```
