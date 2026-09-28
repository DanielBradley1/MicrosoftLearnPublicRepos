<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-sensorcandidate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# sensorCandidate resource type

Namespace: microsoft.graph.security

Represents a Microsoft Defender for Identity sensor that's ready to be activated.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-identitycontainer-list-sensorcandidates?view=graph-rest-1.0) | [microsoft.graph.security.sensorCandidates](https://learn.microsoft.com/en-us/graph/api/resources/security-sensorcandidate?view=graph-rest-1.0) collection | Get a list of the sensorCandidate objects and their properties. |
| [Activate](https://learn.microsoft.com/en-us/graph/api/security-sensorcandidate-activate?view=graph-rest-1.0) | None | Activate Microsoft Defender for Identity sensors. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| computerDnsName | String | The DNS name of the computer associated with the sensor. |
| domainName | String | The domain name of the sensor. |
| id | String | The unique identifier for the sensor candidate. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |
| lastSeenDateTime | DateTimeOffset | The date and time when the sensor was last seen. |
| senseClientVersion | String | The version of the Defender for Identity sensor client. Supports `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.sensorCandidate",
  "id": "String (identifier)",
  "computerDnsName": "String",
  "senseClientVersion": "String",
  "lastSeenDateTime": "String (timestamp)",
  "domainName": "String"
}
```
