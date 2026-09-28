<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-googlecloudresourceevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# googleCloudResourceEvidence resource type

Namespace: microsoft.graph.security

Represents a Google Cloud resource such as compute or Kubernetes cluster identifier.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the evidence was created and added to the alert. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| location | String | The zone or region where the resource is located. |
| locationType | [microsoft.graph.security.googleCloudLocationType](#googlecloudlocationtype-values) | The type of location. The possible values are: `unknown`, `regional`, `zonal`, `global`, `unknownFutureValue`. |
| projectId | String | The Google project ID as defined by the user. |
| projectNumber | Int64 | The project number assigned by Google. |
| remediationStatus | [microsoft.graph.security.evidenceRemediationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceremediationstatus-values) | Status of the remediation action taken. The possible values are: `none`, `remediated`, `prevented`, `blocked`, `notFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| remediationStatusDetails | String | Details about the remediation status. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| resourceName | String | The name of the resource. |
| resourceType | String | The type of the resource. |
| roles | [microsoft.graph.security.evidenceRole](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidencerole-values) collection | One or more roles that an evidence entity represents in an alert. For example, an IP address that is associated with an attacker has the evidence role `Attacker`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| tags | String collection | Array of custom tags associated with an evidence instance. For example, to denote a group of devices or high value assets. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| verdict | [microsoft.graph.security.evidenceVerdict](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceverdict-values) | The decision reached by automated investigation. The possible values are: `unknown`, `suspicious`, `malicious`, `noThreatsFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |

### googleCloudLocationType values

| Member | Description |
| :--- | :--- |
| unknown | An unknown region that is used for forward compatibility. |
| regional | Regional location. |
| zonal | Zonal location. |
| global | Global resource location. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.googleCloudResourceEvidence",
  "createdDateTime": "String (timestamp)",
  "location": "String",
  "locationType": "String",
  "projectId": "String",
  "projectNumber": "Int64",
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "resourceName": "String",
  "resourceType": "String",
  "roles": ["String"],
  "tags": ["String"],
  "verdict": "String"
}
```
