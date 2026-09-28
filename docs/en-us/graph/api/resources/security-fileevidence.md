<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# fileEvidence resource type

Namespace: microsoft.graph.security

A file that is reported in the alert as evidence.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| detectionStatus | microsoft.graph.security.detectionStatus | The status of the detection.The possible values are: `detected`, `blocked`, `prevented`, `unknownFutureValue`. |
| fileDetails | [microsoft.graph.security.fileDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-filedetails?view=graph-rest-1.0) | The file details. |
| mdeDeviceId | String | A unique identifier assigned to a device by Microsoft Defender for Endpoint. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.fileEvidence",
  "createdDateTime": "String (timestamp)",
  "verdict": "String",
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": [
    "String"
  ],
  "tags": [
    "String"
  ],
  "fileDetails": {
    "@odata.type": "microsoft.graph.security.fileDetails"
  },
  "detectionStatus": "String",
  "mdeDeviceId": "String"
}
```
