<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-networkconnectionevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# networkConnectionEvidence resource type

Namespace: microsoft.graph.security

Represents a network connection entity.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the evidence was created and added to the alert. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024 is `2024-01-01T00:00:00Z`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| destinationAddress | [microsoft.graph.security.ipEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-ipevidence?view=graph-rest-1.0) | An entity of type IP that is the destination for this connection. |
| destinationPort | Int32 | The destination port number. For example, `80`. |
| detailedRoles | String collection | Detailed description of the entity role or roles in an alert. Values are free-form. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| protocol | [microsoft.graph.security.protocolType](#protocoltype-values) | The protocol type. Possible values are `tcp`, `udp`, `unknownFutureValue`. |
| remediationStatus | [microsoft.graph.security.evidenceRemediationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceremediationstatus-values) | Status of the remediation action taken. The possible values are: `none`, `remediated`, `prevented`, `blocked`, `notFound`, `unknownFutureValue`, `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| remediationStatusDetails | String | Details about the remediation status. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| roles | [microsoft.graph.security.evidenceRole](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidencerole-values) collection | The role or roles that an evidence entity represents in an alert, for example, an IP address that is associated with an attacker has the evidence role **Attacker**. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| sourceAddress | [microsoft.graph.security.ipEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-ipevidence?view=graph-rest-1.0) | An entity of type IP that is the source for this connection. |
| sourcePort | Int32 | The source port number. For example, `80`. |
| tags | String collection | Array of custom tags associated with an evidence instance, for example, to denote a group of devices and high-value assets. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| verdict | [microsoft.graph.security.evidenceVerdict](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceverdict-values) | The decision reached by automated investigation. The possible values are: `unknown`, `suspicious`, `malicious`, `noThreatsFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |

### protocolType values

| Member | Description |
| :--- | :--- |
| tcp | Reliable, connection-oriented data transfer, essential for web browsing and file transfer. |
| udp | Fast, connectionless data transmission, used for tasks like streaming and gaming. |
| unknownFutureValue | Evolvable enumeration value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.networkConnectionEvidence",
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
  "sourceAddress": {
    "@odata.type": "microsoft.graph.security.ipEvidence"
  },
  "sourcePort": "Int32",
  "destinationAddress": {
    "@odata.type": "microsoft.graph.security.ipEvidence"
  },
  "destinationPort": "Int32",
  "protocol": "String"
}
```
