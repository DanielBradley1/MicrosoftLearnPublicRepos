<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participantendpoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-29 -->

# participantEndpoint resource type

Namespace: microsoft.graph.callRecords

Represents a participant endpoint \(a user or user-like entity\) in a call.

Inherits from [endpoint](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-endpoint?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| associatedIdentity | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Identity associated with the endpoint. |
| cpuCoresCount | Int32 | CPU number of cores used by the media endpoint. |
| cpuName | String | CPU name used by the media endpoint. |
| cpuProcessorSpeedInMhz | Int32 | CPU processor speed used by the media endpoint. |
| feedback | [microsoft.graph.callRecords.userFeedback](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-userfeedback?view=graph-rest-1.0) | The feedback provided by the user of this endpoint about the quality of the session. |
| name | String | Name of the device used by the media endpoint. |
| userAgent | [microsoft.graph.callRecords.userAgent](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-useragent?view=graph-rest-1.0) | User-agent reported by this endpoint. |
| identity \(deprecated\) | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity associated with the endpoint. The **identity** property is deprecated and will stop returning data on June 30, 2026. Going forward, use the **associatedIdentity** property. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "associatedIdentity": {"@odata.type": "microsoft.graph.identity"},
  "cpuCoresCount": "Int32",
  "cpuName": "String",
  "cpuProcessorSpeedInMhz": "Int32",
  "feedback": {"@odata.type": "microsoft.graph.callRecords.userFeedback"},
  "identity": {"@odata.type": "microsoft.graph.identitySet"},
  "name": "String",
  "userAgent": {"@odata.type": "microsoft.graph.callRecords.userAgent"}
}
```
