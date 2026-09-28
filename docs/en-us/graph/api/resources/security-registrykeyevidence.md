<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-registrykeyevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# registryKeyEvidence resource type

Namespace: microsoft.graph.security

A registry key that is reported in the alert as evidence.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| registryHive | String | Registry hive of the key that the recorded action was applied to. |
| registryKey | String | Registry key that the recorded action was applied to. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.registryKeyEvidence",
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
  "registryKey": "String",
  "registryHive": "String"
}
```
