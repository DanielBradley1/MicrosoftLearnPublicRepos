<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationapppolicydetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# authenticationAppPolicyDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides details of the Microsoft Entra policies applied to a user and client authentication app during the authentication step. This object is configured in the **authenticationAppPolicyEvaluationDetails** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| adminConfiguration | authenticationAppAdminConfiguration | The admin configuration of the policy on the user's authentication app. For a policy that does not impact the success/failure of the authentication, the evaluation defaults to `notApplicable`. The possible values are: `notApplicable`, `enabled`, `disabled`, `unknownFutureValue`. |
| authenticationEvaluation | authenticationAppEvaluation | Evaluates the success/failure of the authentication based on the admin configuration of the policy on the user's client authentication app. The possible values are: `success`, `failure`, `unknownFutureValue`. |
| policyName | String | The name of the policy enforced on the user's authentication app. |
| status | authenticationAppPolicyStatus | Refers to whether the policy executed as expected on the user's client authentication app. The possible values are: `unknown`, `appLockOutOfDate`, `appLockEnabled`, `appLockDisabled`, `appContextOutOfDate`, `appContextShown`, `appContextNotShown`, `locationContextOutOfDate`, `locationContextShown`, `locationContextNotShown`, `numberMatchOutOfDate`, `numberMatchCorrectNumberEntered`, `numberMatchIncorrectNumberEntered`, `numberMatchDeny`, `tamperResistantHardwareOutOfDate`, `tamperResistantHardwareUsed`, `tamperResistantHardwareNotUsed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationAppPolicyDetails",
  "policyName": "String",
  "adminConfiguration": "String",
  "status": "String",
  "authenticationEvaluation": "String"
}
```
