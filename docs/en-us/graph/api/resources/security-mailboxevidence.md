<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-mailboxevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-14 -->

# mailboxEvidence resource type

Namespace: microsoft.graph.security

Represents a mailbox that is reported in the alert as evidence.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name associated with the mailbox. |
| primaryAddress | String | The primary email address of the mailbox. |
| upn | String | The user principal name of the mailbox. |
| userAccount | [microsoft.graph.security.userAccount](https://learn.microsoft.com/en-us/graph/api/resources/security-useraccount?view=graph-rest-1.0) | The user account of the mailbox. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.mailboxEvidence",
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
  "displayName": "String",
  "primaryAddress": "String",
  "upn": "String",
  "userAccount": {"@odata.type": "microsoft.graph.security.userAccount"}
}
```
