<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesserviceevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# kubernetesServiceEvidence resource type

Namespace: microsoft.graph.security

Represents a Kubernetes service entity.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clusterIP | [microsoft.graph.security.ipEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-ipevidence?view=graph-rest-1.0) | The service cluster IP. |
| createdDateTime | DateTimeOffset | The date and time when the evidence was created and added to the alert. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| externalIPs | [microsoft.graph.security.ipEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-ipevidence?view=graph-rest-1.0) collection | The service external IPs. |
| labels | [microsoft.graph.security.dictionary](https://learn.microsoft.com/en-us/graph/api/resources/security-dictionary?view=graph-rest-1.0) | The service labels. |
| name | String | The service name. |
| namespace | [microsoft.graph.security.kubernetesNamespaceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesnamespaceevidence?view=graph-rest-1.0) | The service namespace. |
| remediationStatus | [microsoft.graph.security.evidenceRemediationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceremediationstatus-values) | Status of the remediation action taken. The possible values are: `none`, `remediated`, `prevented`, `blocked`, `notFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| remediationStatusDetails | String | Details about the remediation status. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| roles | [microsoft.graph.security.evidenceRole](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidencerole-values) collection | One or more roles that an evidence entity represents in an alert. For example, an IP address that is associated with an attacker has the evidence role `Attacker`. The possible values are: `unknown`, `contextual`, `scanned`, `source`, `destination`, `created`, `added`, `compromised`, `edited`, `attacked`, `attacker`, `commandAndControl`, `loaded`, `suspicious`, `policyViolator`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| selector | [microsoft.graph.security.dictionary](https://learn.microsoft.com/en-us/graph/api/resources/security-dictionary?view=graph-rest-1.0) | The service selector. |
| servicePorts | [microsoft.graph.security.kubernetesServicePort](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesserviceport?view=graph-rest-1.0) collection | The list of service ports. |
| serviceType | [microsoft.graph.security.kubernetesServiceType](#kubernetesservicetype-values) | The service type. The possible values are: `unknown`, `clusterIP`, `externalName`, `nodePort`, `loadBalancer`, `unknownFutureValue`. |
| tags | String collection | Array of custom tags associated with an evidence instance. For example, to denote a group of devices or high value assets. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| verdict | [microsoft.graph.security.evidenceVerdict](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceverdict-values) | The decision reached by automated investigation. The possible values are: `unknown`, `suspicious`, `malicious`, `noThreatsFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |

### kubernetesServiceType values

| Member | Description |
| :--- | :--- |
| unknown | An unknown service type for forward compatibily. |
| clusterIP | Cluster IP type of the service. |
| externalName | External name type of the service. |
| nodePort | Node port type of the service. |
| loadBalancer | Load balancer type of the service. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.kubernetesServiceEvidence",
  "clusterIP": {
    "@odata.type": "microsoft.graph.security.ipEvidence"
  },
  "createdDateTime": "String (timestamp)",
  "externalIPs": [{
    "@odata.type": "microsoft.graph.security.ipEvidence"
  }],
  "labels": {
    "@odata.type": "microsoft.graph.security.dictionary"
  },
  "name": "String",
  "namespace": {
    "@odata.type": "microsoft.graph.security.kubernetesNamespaceEvidence"
  },
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": ["String"],
  "selector": {
    "@odata.type": "microsoft.graph.security.dictionary"
  },
  "servicePorts": [{
    "@odata.type": "microsoft.graph.security.kubernetesServicePort"
  }],
  "serviceType": "String",
  "tags": ["String"],
  "verdict": "String"
}
```
