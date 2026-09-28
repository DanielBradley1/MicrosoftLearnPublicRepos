<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetespodevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# kubernetesPodEvidence resource type

Namespace: microsoft.graph.security

Represents a Kubernetes pod entity.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| containers | [microsoft.graph.security.containerEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-containerevidence?view=graph-rest-1.0) collection | The list of pod containers which are not *init* or *ephemeral* containers. |
| controller | [microsoft.graph.security.kubernetesControllerEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetescontrollerevidence?view=graph-rest-1.0) | The pod controller. |
| createdDateTime | DateTimeOffset | The date and time when the evidence was created and added to the alert. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| ephemeralContainers | [microsoft.graph.security.containerEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-containerevidence?view=graph-rest-1.0) collection | The list of pod *ephemeral* containers. |
| initContainers | [microsoft.graph.security.containerEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-containerevidence?view=graph-rest-1.0) collection | The list of pod *init* containers. |
| labels | [microsoft.graph.security.dictionary](https://learn.microsoft.com/en-us/graph/api/resources/security-dictionary?view=graph-rest-1.0) | The pod labels. |
| name | String | The pod name. |
| namespace | [microsoft.graph.security.kubernetesNamespaceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesnamespaceevidence?view=graph-rest-1.0) | The pod namespace. |
| podIp | [microsoft.graph.security.ipEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-ipevidence?view=graph-rest-1.0) | The pod IP. |
| remediationStatus | [microsoft.graph.security.evidenceRemediationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceremediationstatus-values) | Status of the remediation action taken. The possible values are: `none`, `remediated`, `prevented`, `blocked`, `notFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| remediationStatusDetails | String | Details about the remediation status. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| roles | [microsoft.graph.security.evidenceRole](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidencerole-values) collection | One or more roles that an evidence entity represents in an alert. For example, an IP address that is associated with an attacker has the evidence role `Attacker`. The possible values are: `unknown`, `contextual`, `scanned`, `source`, `destination`, `created`, `added`, `compromised`, `edited`, `attacked`, `attacker`, `commandAndControl`, `loaded`, `suspicious`, `policyViolator`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| serviceAccount | [microsoft.graph.security.kubernetesServiceAccountEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesserviceaccountevidence?view=graph-rest-1.0) | The pod service account. |
| tags | String collection | Array of custom tags associated with an evidence instance. For example, to denote a group of devices or high value assets. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| verdict | [microsoft.graph.security.evidenceVerdict](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceverdict-values) | The decision reached by automated investigation. The possible values are: `unknown`, `suspicious`, `malicious`, `noThreatsFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.kubernetesPodEvidence",
  "containers": [{
    "@odata.type": "microsoft.graph.security.containerEvidence"
  }],
  "controller": {
    "@odata.type": "microsoft.graph.security.kubernetesControllerEvidence"
  },
  "createdDateTime": "String (timestamp)",
  "ephemeralContainers": [{
    "@odata.type": "microsoft.graph.security.containerEvidence"
  }],
  "initContainers": [{
    "@odata.type": "microsoft.graph.security.containerEvidence"
  }],
  "labels": {
    "@odata.type": "microsoft.graph.security.dictionary"
  },
  "name": "String",
  "namespace": {
    "@odata.type": "microsoft.graph.security.kubernetesNamespaceEvidence"
  },
  "podIp": {
    "@odata.type": "microsoft.graph.security.ipEvidence"
  },
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": ["String"],
  "serviceAccount": {
    "@odata.type": "microsoft.graph.security.kubernetesServiceAccountEvidence"
  },
  "tags": ["String"],
  "verdict": "String"
}
```
