<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesclusterevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# kubernetesClusterEvidence resource type

Namespace: microsoft.graph.security

Represents a Kubernetes cluster.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudResource | [microsoft.graph.security.alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0) | The cloud identifier of the cluster. Can be either an [amazonResourceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-amazonresourceevidence?view=graph-rest-1.0), [azureResourceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-azureresourceevidence?view=graph-rest-1.0), or [googleCloudResourceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-googlecloudresourceevidence?view=graph-rest-1.0) object. |
| createdDateTime | DateTimeOffset | The date and time when the evidence was created and added to the alert. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| distribution | String | The distribution type of the cluster. |
| name | String | The cluster name. |
| platform | [microsoft.graph.security.kubernetesPlatform](#kubernetesplatform-values) | The platform the cluster runs on. The possible values are: `unknown`, `aks`, `eks`, `gke`, `arc`, `unknownFutureValue`. |
| remediationStatus | [microsoft.graph.security.evidenceRemediationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceremediationstatus-values) | Status of the remediation action taken. The possible values are: `none`, `remediated`, `prevented`, `blocked`, `notFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| remediationStatusDetails | String | Details about the remediation status. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| roles | [microsoft.graph.security.evidenceRole](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidencerole-values) collection | One or more roles that an evidence entity represents in an alert. For example, an IP address that is associated with an attacker has the evidence role `Attacker`. The possible values are: `unknown`, `contextual`, `scanned`, `source`, `destination`, `created`, `added`, `compromised`, `edited`, `attacked`, `attacker`, `commandAndControl`, `loaded`, `suspicious`, `policyViolator`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| tags | String collection | Array of custom tags associated with an evidence instance. For example, to denote a group of devices or high value assets. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| verdict | [microsoft.graph.security.evidenceVerdict](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceverdict-values) | The decision reached by automated investigation. The possible values are: `unknown`, `suspicious`, `malicious`, `noThreatsFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| version | String | The kubernetes version of the cluster. |

### kubernetesPlatform values

| Member | Description |
| :--- | :--- |
| unknown | An unknown platform for forward compatibility. |
| aks | Azure Kubernetes Service. |
| eks | Amazon Elastic Kubernetes Service. |
| gke | Google Kubernetes Engine. |
| arc | Azure Arc-connected cluster. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.kubernetesClusterEvidence",
  "cloudResource": {
    "@odata.type": "microsoft.graph.security.alertEvidence"
  },
  "createdDateTime": "String (timestamp)",
  "distribution": "String",
  "name": "String",
  "platform": "String",
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": ["String"],
  "tags": ["String"],
  "verdict": "String",
  "version": "String"
}
```
