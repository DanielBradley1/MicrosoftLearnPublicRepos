<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-activedirectorydomainevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-06 -->

# activeDirectoryDomainEvidence resource type

Namespace: microsoft.graph.security

A file that is reported in the alert as evidence.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0), which represents evidence related to an [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeDirectoryDomainName | String | The name of the Active Directory domain. |
| createdDateTime | DateTimeOffset | The date and time when the evidence was created and added to the alert. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| detailedRoles | String collection | Detailed roles of the evidence in the alert. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| remediationStatus | [microsoft.graph.security.evidenceRemediationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceremediationstatus-values) | The status of the remediation action taken. The possible values are: `none`, `remediated`, `prevented`, `blocked`, `notFound`, `active`, `pendingApproval`, `declined`, `notRemediated`, `running`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| remediationStatusDetails | String | Details about the remediation status. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| roles | [microsoft.graph.security.evidenceRole](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidencerole-values) collection | One or more roles that an evidence entity represents in an alert. For example, an IP address that is associated with an attacker has the evidence role `Attacker`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| tags | String collection | Array of custom tags associated with an evidence instance. For example, to denote a group of devices or high value assets. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| trustedDomains | microsoft.graph.security.activeDirectoryDomainEvidence collection | List of trusted domains. |
| verdict | [microsoft.graph.security.evidenceVerdict](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceverdict-values) | The decision reached by automated investigation. The possible values are: `unknown`, `suspicious`, `malicious`, `noThreatsFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.activeDirectoryDomainEvidence",
  "createdDateTime": "String (timestamp)",
  "verdict": "String",
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": [
    "String"
  ],
  "detailedRoles": [
    "String"
  ],
  "tags": [
    "String"
  ],
  "activeDirectoryDomainName": "String",
  "trustedDomains": [{"@odata.type": "microsoft.graph.security.activeDirectoryDomainEvidence"}],
}
```
