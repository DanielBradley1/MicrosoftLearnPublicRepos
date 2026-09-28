<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# oneDriveForBusinessProtectionPolicy resource type

Namespace: microsoft.graph

Contains details about protection policies applied to Microsoft 365 data in an organization. Protection policies are defined by the Global Admin \(or the SharePoint Online Admin or Exchange Online Admin\) and include what data to protect, when to protect it, and for what time period to retain the protected data for a single Microsoft 365 service.

Inherits from [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-onedriveforbusinessprotectionpolicies?view=graph-rest-1.0) | [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0) | Create a new [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0). |
| [Update](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessprotectionpolicy-update?view=graph-rest-1.0) | [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0) | Update the properties of a [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the protection rule associated with the policy. |
| displayName | String | The name of the policy to be created. |
| createdDateTime | DateTimeOffset | The time of creation of the policy. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of person who created the policy. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who last modified the policy. |
| lastModifiedDateTime | DateTimeOffset | The timestamp of the last modification of the policy. |
| status | [protectionPolicyStatus](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0#protectionpolicystatus-values) | Status of the policy. The value is the aggregated status of the protection units. The possible values are: `inactive`, `activeWithErrors`, `updating`, `active`, `unknownFutureValue`. |

### protectionPolicyStatus values

| Member | Description |
| :--- | :--- |
| active | All units are protected. |
| activeWithErrors | Some units are protected and others are unprotected. |
| inactive | All units are unprotected. |
| updating | Some or all units are in a `protectRequested`, `unprotectRequested`, or `removeRequested` state. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| driveInclusionRules | [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0) collection | Contains the details of the Onedrive for Business protection rule. |
| driveProtectionUnits | [driveProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunit?view=graph-rest-1.0) collection | Contains the protection units associated with a OneDrive for Business protection policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.oneDriveForBusinessProtectionPolicy",
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
