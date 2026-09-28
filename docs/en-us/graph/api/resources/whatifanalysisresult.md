<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/whatifanalysisresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# whatIfAnalysisResult resource type

Namespace: microsoft.graph

Represents the result of a Conditional Access What If evaluation, which indicates the policies that would apply based on the sign-in details you provide. For more information, see the [Conditional Access Policy What If tool](https://learn.microsoft.com/en-us/entra/identity/conditional-access/what-if-tool).

Inherits from [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Evaluate](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-1.0) | [whatIfAnalysisResult](https://learn.microsoft.com/en-us/graph/api/resources/whatifanalysisresult?view=graph-rest-1.0) collection | List the results of the What If evaluation of Conditional Access Policies targeting a sign-in attempt. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| analysisReasons | whatIfAnalysisReasons | Specifies the reasons why a policy didn't apply. `analysisReasons` is set to `notSet` when `policyApplies` is `true` and one of the following values when `policyApplies` is `false`: `notEnoughInformation`, `invalidCondition`, `users`, `workloadIdentities`, `application`, `userActions`, `authenticationContext`, `devicePlatform`, `devices`, `clientApps`, `location`, `signInRisk`, `emptyPolicy`, `invalidPolicy`, `policyNotEnabled`, `userRisk`, `time`, `insiderRisk`, `authenticationFlow`, `unknownFutureValue`. |
| conditions | [conditionalAccessConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessconditionset?view=graph-rest-1.0) | Specifies the rules that must be met for the policy to apply. Inherited from [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0). |
| description | String | Not used. Inherited from [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0). |
| displayName | String | Specifies a display name for the conditionalAccessPolicy object. Inherited from [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0). |
| grantControls | [conditionalAccessGrantControls](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessgrantcontrols?view=graph-rest-1.0) | Specifies the grant controls that must be fulfilled to pass the policy. Inherited from [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0). |
| id | String | Specifies the identifier of a conditionalAccessPolicy object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| modifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0). |
| policyApplies | Boolean | Specifies whether the policy applies to the sign-in properties provided in the request body. If `policyApplies` is `true`, the policy applies to the sign-in based on the sign-in properties provided. If `policyApplies` is `false`, the policy doesn't apply to the sign-in based on the sign-in properties provided and the `analysisReasons` property is populated to show the reason for the policy not applying. |
| sessionControls | [conditionalAccessSessionControls](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrols?view=graph-rest-1.0) | Specifies the session controls that are enforced after sign-in. Inherited from [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0). |
| state | conditionalAccessPolicyState | Specifies the state of the conditionalAccessPolicy object. Inherited from [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0). The possible values are: `enabled`, `disabled`, `enabledForReportingButNotEnforced`, `unknownFutureValue`. |
| templateId | String | Specifies the unique identifier of a [Conditional Access template](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0). Inherited from [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.whatIfAnalysisResult",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "description": "String",
  "state": "String",
  "conditions": {
    "@odata.type": "microsoft.graph.conditionalAccessConditionSet"
  },
  "grantControls": {
    "@odata.type": "microsoft.graph.conditionalAccessGrantControls"
  },
  "sessionControls": {
    "@odata.type": "microsoft.graph.conditionalAccessSessionControls"
  },
  "policyApplies": "Boolean",
  "analysisReasons": "String",
  "templateId": "String"
}
```
