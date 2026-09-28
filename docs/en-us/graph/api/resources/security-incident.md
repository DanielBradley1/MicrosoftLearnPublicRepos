<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-22 -->

# incident resource type

Namespace: microsoft.graph.security

An incident in Microsoft 365 Defender is a collection of correlated [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) instances and associated metadata that reflects the story of an attack on a tenant.

Microsoft 365 services and apps create alerts when they detect a suspicious or malicious event or activity. Individual alerts provide valuable clues about a completed or ongoing attack. However, attacks typically employ various techniques against different types of entities, such as devices, users, and mailboxes. The result is multiple alerts for multiple entities in your tenant. Because piecing the individual alerts together to gain insight into an attack can be challenging and time-consuming, Microsoft 365 Defender automatically aggregates the alerts and their associated information into an incident.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List incidents](https://learn.microsoft.com/en-us/graph/api/security-list-incidents?view=graph-rest-1.0) | [microsoft.graph.security.incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) collection | Get a list of [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) objects that Microsoft 365 Defender created to track attacks in an organization. |
| [Get incident](https://learn.microsoft.com/en-us/graph/api/security-incident-get?view=graph-rest-1.0) | [microsoft.graph.security.incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) | Read the properties and relationships of an [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) object. |
| [Update incident](https://learn.microsoft.com/en-us/graph/api/security-incident-update?view=graph-rest-1.0) | [microsoft.graph.security.incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) | Update the properties of an [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) object. |
| [Create comment for incident](https://learn.microsoft.com/en-us/graph/api/security-incident-post-comments?view=graph-rest-1.0) | [alertComment](https://learn.microsoft.com/en-us/graph/api/resources/security-alertcomment?view=graph-rest-1.0) | Create a comment for an existing [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) based on the specified incident **id** property. |
| [Merge incidents](https://learn.microsoft.com/en-us/graph/api/security-incident-mergeincidents?view=graph-rest-1.0) | [microsoft.graph.security.mergeResponse](https://learn.microsoft.com/en-us/graph/api/resources/security-mergeresponse?view=graph-rest-1.0) | Merge multiple [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) resources into a single incident. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | String | Owner of the incident, or null if no owner is assigned. Free editable text. |
| classification | microsoft.graph.security.alertClassification | The specification for the incident. The possible values are: `unknown`, `falsePositive`, `truePositive`, `informationalExpectedActivity`, `unknownFutureValue`. |
| comments | [microsoft.graph.security.alertComment](https://learn.microsoft.com/en-us/graph/api/resources/security-alertcomment?view=graph-rest-1.0) collection | Array of comments created by the Security Operations \(SecOps\) team when the incident is managed. |
| createdDateTime | DateTimeOffset | Time when the incident was first created. |
| customTags | String collection | Array of custom tags associated with an incident. |
| description | String | Description of the incident. |
| determination | microsoft.graph.security.alertDetermination | Specifies the determination of the incident. The possible values are: `unknown`, `apt`, `malware`, `securityPersonnel`, `securityTesting`, `unwantedSoftware`, `other`, `multiStagedAttack`, `compromisedUser`, `phishing`, `maliciousUserActivity`, `clean`, `insufficientData`, `confirmedActivity`, `lineOfBusinessApplication`, `unknownFutureValue`. |
| displayName | String | The incident name. |
| id | String | Unique identifier to represent the incident. |
| incidentWebUrl | String | The URL for the incident page in the Microsoft 365 Defender portal. |
| lastModifiedBy | String | The identity that last modified the incident. |
| lastUpdateDateTime | DateTimeOffset | Time when the incident was last updated. |
| priorityScore | Int | A priority score for the incident from 0 to 100, with > 85 being the top priority, 15 - 85 medium priority, and < 15 low priority. This score is generated using machine learning and is based on multiple factors, including severity, disruption impact, threat intelligence, alert types, asset criticality, threat analytics, incident rarity, and additional priority signals. The value can also be `null` which indicates the feature is not open for the tenant or the value of the score is pending calculation. |
| redirectIncidentId | String | Only populated in case an incident is grouped with another incident, as part of the logic that processes incidents. In such a case, the **status** property is `redirected`. |
| resolvingComment | String | User input that explains the resolution of the incident and the classification choice. This property contains free editable text. |
| severity | alertSeverity | Indicates the possible impact on assets. The higher the severity, the bigger the impact. Typically higher severity items require the most immediate attention. The possible values are: `unknown`, `informational`, `low`, `medium`, `high`, `unknownFutureValue`. |
| status | [microsoft.graph.security.incidentStatus](#incidentstatus-values) | The status of the incident. The possible values are: `active`, `resolved`, `inProgress`, `redirected`, `unknownFutureValue`, and `awaitingAction`. |
| summary | String | The overview of an attack. When applicable, the summary contains details of what occurred, impacted assets, and the type of attack. |
| systemTags | String collection | The system tags associated with the incident. |
| tenantId | String | The Microsoft Entra tenant in which the alert was created. |

### incidentStatus values

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Use the `Prefer: include-unknown-enum-members` request header to get the following values in this evolvable enum: `awaitingAction`.

| Member | Description |
| :--- | :--- |
| active | The incident is in active state. |
| resolved | The incident is in resolved state. |
| inProgress | The incident is in mitigation progress. |
| redirected | The incident was merged with another incident. The target incident ID appears in the **redirectIncidentId** property. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| awaitingAction | This incident requires actions from Defender Experts awaiting your action. Only Microsoft 365 Defender experts can set this status. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| alerts | [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) collection | The list of related alerts. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.incident",
  "assignedTo": "String",
  "classification": "String",
  "comments": [{"@odata.type": "microsoft.graph.security.alertComment"}],
  "createdDateTime": "String (timestamp)",
  "customTags": ["String"],
  "description" : "String",
  "determination": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "incidentWebUrl": "String",
  "lastModifiedBy": "String",
  "lastUpdateDateTime": "String (timestamp)",
  "redirectIncidentId": "String",
  "resolvingComment": "String",
  "severity": "String",
  "status": "String",
  "summary": "String",
  "systemTags" : ["String"],
  "tenantId": "String",
  "priorityScore": "Int"
}
```
