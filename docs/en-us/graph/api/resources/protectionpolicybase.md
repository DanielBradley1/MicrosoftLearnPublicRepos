<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# protectionPolicyBase resource type

Namespace: microsoft.graph

Contains details about protection policies applied to Microsoft 365 data in an organization. Protection policies are defined by the Global Admin \(or the SharePoint Online Admin or Exchange Online Admin\) and include what data to protect, when to protect it, and for what time period to retain the protected data for a single Microsoft 365 service.

Base type for [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0), [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0), and [onedriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-protectionpolicies?view=graph-rest-1.0) | [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) collection | Get a list of the [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/protectionpolicybase-get?view=graph-rest-1.0) | [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) | Read the properties and relationships of a [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/protectionpolicybase-delete?view=graph-rest-1.0) | None | Delete a [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) object. |
| [Activate](https://learn.microsoft.com/en-us/graph/api/protectionpolicybase-activate?view=graph-rest-1.0) | [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) | Activate an inactive protection policy. |
| [Deactivate](https://learn.microsoft.com/en-us/graph/api/protectionpolicybase-deactivate?view=graph-rest-1.0) | [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) | Deactivate an active protection policy. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the protection rule associated with the policy. |
| displayName | String | The name of the policy to be created. |
| createdDateTime | DateTimeOffset | The time of creation of the policy. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of person who created the policy. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who last modified the policy. |
| lastModifiedDateTime | DateTimeOffset | The timestamp of the last modification of the policy. |
| retentionSettings | [retentionSetting](https://learn.microsoft.com/en-us/graph/api/resources/retentionsetting?view=graph-rest-1.0) collection | Contains the retention setting details for the policy. |
| status | [protectionPolicyStatus](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0#protectionpolicystatus-values) | The aggregated status of the protection units associated with the policy. The possible values are: `inactive`, `activeWithErrors`, `updating`, `active`, `unknownFutureValue`. |

### protectionPolicyStatus values

| Member | Description |
| :--- | :--- |
| active | All units are protected. |
| activeWithErrors | Some units are protected and others are unprotected. |
| inactive | All units are unprotected. |
| updating | Some or all units are in a `protectRequested`, `unprotectRequested`, or `removeRequested` state. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.protectionPolicyBase",
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
  },
  "retentionSettings": [
    {
      "@odata.type": "microsoft.graph.retentionSetting"
    }
  ]
}
```
