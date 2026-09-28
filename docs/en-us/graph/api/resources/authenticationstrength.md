<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrength?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# authenticationStrength resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the custom authentication strength enforced in a conditional access policy. This object is configured in the **authenticationStrength** property of [appliedConditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appliedconditionalaccesspolicy?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationStrengthId | String | Identifier of the authentication strength. |
| authenticationStrengthResult | authenticationStrengthResult | The result of the authentication strength. The possible values are: `notSet`, `skippedForProofUp`, `satisfied`, `singleChallengeRequired`, `multipleChallengesRequired`, `singleRegistrationRequired`, `multipleRegistrationsRequired`, `cannotSatisfyDueToCombinationConfiguration`, `cannotSatisfy`, `unknownFutureValue`. |
| displayName | String | The name of the authentication strength. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationStrength",
  "authenticationStrengthId": "String",
  "authenticationStrengthResult": "String",
  "displayName": "String"
}
```
