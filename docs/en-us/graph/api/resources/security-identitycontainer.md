<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-identitycontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# identityContainer resource type

Namespace: microsoft.graph.security

Represents a container for security identities APIs that currently exposes the [healthIssues](https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0) relationship.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| healthIssues | [microsoft.graph.security.healthIssue](https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0) collection | Represents potential issues identified by Microsoft Defender for Identity within a customer's Microsoft Defender for Identity configuration. |
| identityAccounts | [microsoft.graph.security.identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0) collection | Represents an identity's details in the context of Microsoft Defender for Identity. |
| sensors | [microsoft.graph.security.sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) collection | Represents a customer's Microsoft Defender for Identity sensors. |
| sensorCandidates | [microsoft.graph.security.sensorCandidate](https://learn.microsoft.com/en-us/graph/api/resources/security-sensorcandidate?view=graph-rest-1.0) collection | Represents Microsoft Defender for Identity sensors that are ready to be activated. |
| sensorCandidateActivationConfiguration | [microsoft.graph.security.sensorCandidateActivationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-sensorcandidateactivationconfiguration?view=graph-rest-1.0) collection | Represents the activation mode of a Microsoft Defender for Identity sensor. |
| settings | [microsoft.graph.security.settingsContainer](https://learn.microsoft.com/en-us/graph/api/resources/security-settingscontainer?view=graph-rest-1.0) | Represents a container for security identities settings APIs. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.identityContainer"
}
```
