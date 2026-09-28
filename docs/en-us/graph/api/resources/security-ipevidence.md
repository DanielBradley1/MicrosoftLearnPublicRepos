<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ipevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# ipEvidence resource type

Namespace: microsoft.graph.security

An IP Address that is reported in the alert as evidence.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| countryLetterCode | String | The two-letter country code according to ISO 3166 format, for example: `US`, `UK`, `CA`, etc. |
| ipAddress | String | The value of the IP Address, can be either in V4 address or V6 address format. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ipEvidence",
  "createdDateTime": "String (timestamp)",
  "verdict": "String",
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": [
    "String"
  ],
  "tags": [
    "String"
  ],
  "ipAddress": "String",
  "countryLetterCode": "String"
}
```
