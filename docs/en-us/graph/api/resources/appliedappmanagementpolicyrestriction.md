<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appliedappmanagementpolicyrestriction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# appliedAppManagementPolicyRestriction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an app management policy restriction applied to an audited activity.

This complex type is returned by the **appliedAppManagementPolicyRestrictions** property of the [appManagementAudit](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementaudit?view=graph-rest-beta) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attemptedChanges | [microsoft.graph.Dictionary](https://learn.microsoft.com/en-us/graph/api/resources/dictionary?view=graph-rest-beta) | The changes attempted during the activity. |
| auditResult | [appManagementAuditLogAuditResult](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#appmanagementauditlogauditresult-values) | The result that the restriction would have produced if it were enabled. This property is applicable only when **restrictionState** is `audit`. The possible values are: `notApplicable`, `wouldHaveBeenAllowed`, `wouldHaveBeenBlocked`, `unknownFutureValue`. |
| policyId | String | The unique identifier of the policy that contains the restriction. |
| policyType | [appManagementAuditLogPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#appmanagementauditlogpolicytype-values) | The type of policy that contains the restriction. The possible values are: `defaultEntraId`, `tenant`, `app`, `unknownFutureValue`. |
| restrictionDetails | [microsoft.graph.Dictionary](https://learn.microsoft.com/en-us/graph/api/resources/dictionary?view=graph-rest-beta) | Details about the restriction. |
| restrictionResult | [appManagementAuditLogRestrictionResult](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#appmanagementauditlogrestrictionresult-values) | The result of the restriction. The possible values are: `allowed`, `blocked`, `unknownFutureValue`. |
| restrictionState | [appManagementAuditLogRestrictionState](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#appmanagementauditlogrestrictionstate-values) | The state of the restriction at the time of the activity. The possible values are: `enabled`, `disabled`, `audit`, `unknownFutureValue`. |
| restrictionType | String | The type of restriction applied to the activity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appliedAppManagementPolicyRestriction",
  "restrictionType": "String",
  "restrictionState": "String",
  "restrictionResult": "String",
  "auditResult": "String",
  "policyId": "String",
  "policyType": "String",
  "restrictionDetails": {
    "@odata.type": "microsoft.graph.Dictionary"
  },
  "attemptedChanges": {
    "@odata.type": "microsoft.graph.Dictionary"
  }
}
```
