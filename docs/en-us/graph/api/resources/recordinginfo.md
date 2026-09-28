<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recordinginfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# recordingInfo resource type

Namespace: microsoft.graph

Represents recording information for a participant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identities of the recording initiator. |
| recordingStatus | String | The possible values are: `unknown`, `notRecording`, `recording`, or `failed`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "initiator": {"@odata.type": "#microsoft.graph.identitySet"},
  "recordingStatus": "unknown | notRecording | recording | failed"
}
```
