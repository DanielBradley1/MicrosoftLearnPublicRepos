<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# exchangeProtectionPolicy resource type

Namespace: microsoft.graph

Represents the plan defined by the Exchange Online Admin to protect Exchange Online. The Exchange protection policy defines what mailbox data to protect, when to protect it, and for what time period to retain the protected data.

Inherits from [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-exchangeprotectionpolicies?view=graph-rest-1.0) | [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0) | Create a new [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0). |
| [Update](https://learn.microsoft.com/en-us/graph/api/exchangeprotectionpolicy-update?view=graph-rest-1.0) | [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0) | Update the properties of an [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the protection rule associated to the policy. |
| displayName | String | Name of the policy to be created. |
| createdDateTime | DateTimeOffset | The time of creation of the policy. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of person who created the policy. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who last modified the policy. |
| lastModifiedDateTime | DateTimeOffset | The timestamp of the last modification of the policy. |
| status | [protectionPolicyStatus](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0#protectionpolicystatus-values) | Status of the policy. This value is an aggregated status of the protection units. The possible values are: `inactive`, `activeWithErrors`, `updating`, `active`, `unknownFutureValue`. |

### protectionPolicyStatus values

| Member | Description |
| :--- | :--- |
| active | All units are protected. |
| activeWithErrors | Some units are protected while others are unprotected. |
| inactive | All units are unprotected. |
| updating | Some or all units are in a `protectRequested`, `unprotectRequested`, or `removeRequested` state. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| mailboxInclusionRules | [mailboxProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionrule?view=graph-rest-1.0) collection | The rules associated with the Exchange protection policy. |
| mailboxProtectionUnits | [mailboxProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-1.0) collection | The protection units \(mailboxes\) that are protected under the Exchange protection policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.exchangeProtectionPolicy",
  "id": "String (identifier)",
  "displayName": "String",
  "status": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```
