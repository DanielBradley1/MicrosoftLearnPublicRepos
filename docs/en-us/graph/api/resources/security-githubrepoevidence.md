<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-githubrepoevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# gitHubRepoEvidence resource type

Namespace: microsoft.graph.security

Represents a repository in GitHub.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| baseUrl | String | The base URL of the web page for the repository. |
| createdDateTime | DateTimeOffset | The date and time when the evidence was created and added to the alert. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024 is `2024-01-01T00:00:00Z`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| detailedRoles | String collection | Detailed description of the entity role or roles in an alert. Values are free-form. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| login | String | The login \(name\) of the repository. |
| owner | String | The login of the owner of the repository. |
| ownerType | String | The type of owner of the repository, for example, `User` or `Organization`. |
| remediationStatus | [microsoft.graph.security.evidenceRemediationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceremediationstatus-values) | Status of the remediation action taken. The possible values are: `none`, `remediated`, `prevented`, `blocked`, `notFound`, `unknownFutureValue`, `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| remediationStatusDetails | String | Details about the remediation status. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| repoId | String | The unique and immutable ID of the GitHub repository. |
| roles | [microsoft.graph.security.evidenceRole](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidencerole-values) collection | The role or roles that an evidence entity represents in an alert, for example, an IP address that is associated with an attacker has the evidence role **Attacker**. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| tags | String collection | Array of custom tags associated with an evidence instance, for example, to denote a group of devices and high-value assets. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| verdict | [microsoft.graph.security.evidenceVerdict](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceverdict-values) | The decision reached by automated investigation. The possible values are: `unknown`, `suspicious`, `malicious`, `noThreatsFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.gitHubRepoEvidence",
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
  "repoId": "String",
  "login": "String",
  "owner": "String",
  "ownerType": "String",
  "baseUrl": "String"
}
```
