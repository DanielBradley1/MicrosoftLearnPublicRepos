<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-userevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# userEvidence resource type

Namespace: microsoft.graph.security

A user that is reported in the alert as evidence.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userAccount | [microsoft.graph.security.userAccount](https://learn.microsoft.com/en-us/graph/api/resources/security-useraccount?view=graph-rest-1.0) | The user account details. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.userEvidence",
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
  "userAccount": {
    "@odata.type": "microsoft.graph.security.userAccount"
  }
}
```
