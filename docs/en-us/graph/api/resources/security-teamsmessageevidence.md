<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-teamsmessageevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-13 -->

# teamsMessageEvidence resource type

Namespace: microsoft.graph.security

Represents a Microsoft Teams message that is reported as part of a security detection alert.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| campaignId | String | The identifier of the campaign that this Teams message is part of. |
| channelId | String | The channel ID associated with this Teams message. |
| createdDateTime | DateTimeOffset | The date and time when the evidence was created and added to the alert. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| deliveryAction | microsoft.graph.security.teamsMessageDeliveryAction | The delivery action of this Teams message. The possible values are: `unknown`, `deliveredAsSpam`, `delivered`, `blocked`, `replaced`, `unknownFutureValue`. |
| deliveryLocation | microsoft.graph.security.teamsDeliveryLocation | The delivery location of this Teams message. The possible values are: `unknown`, `teams`, `quarantine`, `failed`, `unknownFutureValue`. |
| detailedRoles | String collection | The detailed description of the entity roles in an alert. Values are free-form. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| files | [microsoft.graph.security.fileEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-fileevidence?view=graph-rest-1.0) collection | The list of file entities that are attached to this Teams message. |
| groupId | String | The identifier of the team or group that this message is part of. |
| isExternal | Boolean | Indicates whether the message is owned by the organization that reported the security detection alert. |
| isOwned | Boolean | Indicates whether the message is owned by your organization. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the message was last edited. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| messageDirection | microsoft.graph.security.antispamTeamsDirection | The direction of the Teams message. The possible values are: `unknown`, `inbound`, `outbound`, `intraorg`, `unknownFutureValue`. |
| messageId | String | Message identifier unique within the thread. |
| owningTenantId | String | Tenant ID \(GUID\) of the owner of the message. |
| parentMessageId | String | Identifier of the message to which the current message is a reply; otherwise, it's the same as the **messageId**. |
| receivedDateTime | DateTimeOffset | The received date of this message. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| recipients | String collection | The recipients of this Teams message. |
| remediationStatus | [microsoft.graph.security.evidenceRemediationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceremediationstatus-values) | Status of the remediation action taken. The possible values are: `none`, `remediated`, `prevented`, `blocked`, `notFound`, `unknownFutureValue`, `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| remediationStatusDetails | String | Details about the remediation status. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| roles | [microsoft.graph.security.evidenceRole](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidencerole-values) collection | One or more roles that an evidence entity represents in an alert; for example, an IP address associated with an attacker has the evidence role `Attacker`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| senderFromAddress | String | The SMTP format address of the sender. |
| senderIP | String | The IP address of the sender. |
| sourceAppName | String | Source of the message; for example, `desktop` and `mobile`. |
| sourceId | String | The source ID of this Teams message. |
| subject | String | The subject of this Teams message. |
| suspiciousRecipients | String collection | The list of recipients who were detected as suspicious. |
| tags | String collection | Array of custom tags associated with an evidence instance; for example, to denote a group of devices or high-value assets. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| threadId | String | Identifier of the channel or chat that this message is part of. |
| threadType | String | The Teams message type. Supported values are: `Chat`, `Topic`, `Space`, and `Meeting`. |
| urls | [microsoft.graph.security.urlEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-urlevidence?view=graph-rest-1.0) collection | The URLs contained in this Teams message. |
| verdict | [microsoft.graph.security.evidenceVerdict](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceverdict-values) | The decision reached by automated investigation. The possible values are: `unknown`, `suspicious`, `malicious`, `noThreatsFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.teamsMessageEvidence",
  "campaignId": "String",
  "channelId": "String",
  "createdDateTime": "String (timestamp)",
  "deliveryAction": "String",
  "deliveryLocation": "String",
  "files": [{"@odata.type": "microsoft.graph.security.fileEvidence"}],
  "groupId": "String",
  "isExternal": "Boolean",
  "isOwned": "Boolean",
  "lastModifiedDateTime": "String (timestamp)",
  "messageDirection": "String",
  "messageId": "String",
  "owningTenantId": "String",
  "parentMessageId": "String",
  "receivedDateTime": "String (timestamp)",
  "recipients": ["String"],
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": ["String"],
  "senderFromAddress": "String",
  "senderIP": "String",
  "sourceAppName": "String",
  "sourceId": "String",
  "subject": "String",
  "suspiciousRecipients": ["String"],
  "tags": ["String"],
  "threadId": "String",
  "threadType": "String",
  "urls": [{"@odata.type": "microsoft.graph.security.urlEvidence"}],
  "verdict": "String"
}
```
