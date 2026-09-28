<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-nicevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-16 -->

# nicEvidence resource type

Namespace: microsoft.graph.security

Represents a NIC \(v2\) entity that is reported as part of the security detection alert.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| macAddress | String | The MAC address of the NIC. |
| ipAddress | [microsoft.graph.security.ipEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-ipevidence?view=graph-rest-1.0) | The current IP address of the NIC. |
| vlans | Collection\(String\) | The current virtual local area networks of the NIC. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.nicEvidence",
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
  "macAddress": "String",
  "ipAddress": {
    "@odata.type": "microsoft.graph.security.ipEvidence"
  },
  "vlans": [
    "String"
  ]
}
```
