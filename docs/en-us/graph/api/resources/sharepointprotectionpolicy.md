<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# sharePointProtectionPolicy resource type

Namespace: microsoft.graph

Represents a plan defined by the SharePoint Online admin to protect SharePoint Online, including what data to protect, when to protect it, and for what time period to retain the protected data. Currently, policies are supported only for SharePoint Online sites in the main geolocation only; multi-geo tenants aren't supported.

Inherits from [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-sharepointprotectionpolicies?view=graph-rest-1.0) | [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0) | Create a new [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0). |
| [Update](https://learn.microsoft.com/en-us/graph/api/sharepointprotectionpolicy-update?view=graph-rest-1.0) | [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0) | Update the properties of a [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the protection rule associated to the policy. |
| displayName | String | The name of the policy being created. |
| createdDateTime | DateTimeOffset | The time of creation of the policy. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of person who created the policy. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of person who modified the policy. |
| lastModifiedDateTime | DateTimeOffset | The timestamp of the last modification of the policy. |
| retentionSettings | [retentionSetting](https://learn.microsoft.com/en-us/graph/api/resources/retentionsetting?view=graph-rest-1.0) collection | Retention settings for the policy. |
| status | [protectionPolicyStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0#protectionpolicystatus-values) | The status of the policy. The value is an aggregated status of the protection units. The possible values are: `inactive`, `activeWithErrors`, `updating`, `active`, `unknownFutureValue`. |

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
| siteInclusionRules | [siteProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0) collection | The rules associated with the SharePoint Protection policy. |
| siteProtectionUnits | [siteProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunit?view=graph-rest-1.0) collection | The protection units \(sites\) that are protected under the site protection policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointProtectionPolicy",
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
