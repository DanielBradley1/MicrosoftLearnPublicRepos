<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-serviceprincipalevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# servicePrincipalEvidence resource type

Namespace: microsoft.graph.security

Represents a service principal reported in a security detection alert.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The unique identifier for the associated application, represented by its **appId** property. |
| appOwnerTenantId | String | The tenant ID where the application is registered. |
| createdDateTime | DateTimeOffset | The date and time when the evidence was created and added to the alert. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024 is `2024-01-01T00:00:00Z`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| detailedRoles | String collection | Detailed description of the entity role or roles in an alert. Values are free-form. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| remediationStatus | [microsoft.graph.security.evidenceRemediationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceremediationstatus-values) | Status of the remediation action taken. The possible values are: `none`, `remediated`, `prevented`, `blocked`, `notFound`, `unknownFutureValue`, `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| remediationStatusDetails | String | Details about the remediation status. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| roles | [microsoft.graph.security.evidenceRole](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidencerole-values) collection | The role or roles that an evidence entity represents in an alert, for example, an IP address that is associated with an attacker has the evidence role **Attacker**. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| servicePrincipalName | String | The display name for the service principal. |
| servicePrincipalObjectId | String | The unique identifier for the service principal. |
| servicePrincipalType | [microsoft.graph.security.servicePrincipalType](#serviceprincipaltype-values) | The service principal type. Possible values are: `unknown`, `application`, `managedIdentity`, `legacy`, `unknownFutureValue`. |
| tags | String collection | Array of custom tags associated with an evidence instance, for example, to denote a group of devices and high-value assets. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |
| tenantId | String | The Microsoft Entra tenant ID of the service principal. |
| verdict | [microsoft.graph.security.evidenceVerdict](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0#evidenceverdict-values) | The decision reached by automated investigation. The possible values are: `unknown`, `suspicious`, `malicious`, `noThreatsFound`, `unknownFutureValue`. Inherited from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0). |

### servicePrincipalType values

| Member | Description |
| :--- | :--- |
| unknown | The service principal type is unknown. |
| application | The local representation or application instance of a global application object in a single tenant or directory. |
| managedIdentity | The service principal is used to represent a managed identity. |
| legacy | The service principal is a legacy app, which represents either an app created before app registrations were introduced or an app created through legacy experiences. |
| unknownFutureValue | Evolvable enumeration value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.servicePrincipalEvidence",
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
  "servicePrincipalName": "String",
  "servicePrincipalObjectId": "String",
  "appId": "String",
  "appOwnerTenantId": "String",
  "tenantId": "String",
  "servicePrincipalType": "String"
}
```
