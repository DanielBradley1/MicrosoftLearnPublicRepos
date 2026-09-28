<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-processevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# processEvidence resource type

Namespace: microsoft.graph.security

Represents a process that is reported in the alert as evidence.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| detectionStatus | microsoft.graph.security.detectionStatus | The status of the detection.The possible values are: `detected`, `blocked`, `prevented`, `unknownFutureValue`. |
| imageFile | [microsoft.graph.security.fileDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-filedetails?view=graph-rest-1.0) | Image file details. |
| mdeDeviceId | String | A unique identifier assigned to a device by Microsoft Defender for Endpoint. |
| parentProcessCreationDateTime | DateTimeOffset | Date and time when the parent of the process was created. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| parentProcessId | Int64 | Process ID \(PID\) of the parent process that spawned the process. |
| parentProcessImageFile | [microsoft.graph.security.fileDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-filedetails?view=graph-rest-1.0) | Parent process image file details. |
| processCommandLine | String | Command line used to create the new process. |
| processCreationDateTime | DateTimeOffset | Date and time when the process was created. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| processId | Int64 | Process ID \(PID\) of the newly created process. |
| userAccount | [microsoft.graph.security.userAccount](https://learn.microsoft.com/en-us/graph/api/resources/security-useraccount?view=graph-rest-1.0) | User details of the user that ran the process. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.processEvidence",
  "createdDateTime": "String (timestamp)",
  "detectionStatus": "String",
  "imageFile": {"@odata.type": "microsoft.graph.security.fileDetails"},
  "mdeDeviceId": "String",
  "parentProcessCreationDateTime": "String (timestamp)",
  "parentProcessId": "Int64",
  "parentProcessImageFile": {"@odata.type": "microsoft.graph.security.fileDetails"},
  "processCommandLine": "String",
  "processCreationDateTime": "String (timestamp)",
  "processId": "Int64",
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": ["String"],
  "tags": ["String"],
  "userAccount": {"@odata.type": "microsoft.graph.security.userAccount"},
  "verdict": "String"
}
```
