<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-invokeactionresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# invokeActionResult resource type

Namespace: microsoft.graph.security

Represents the invoke action result after [disabling an identity account](https://learn.microsoft.com/en-us/graph/api/security-identityaccounts-invokeaction?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountId | String | The account ID. |
| action | microsoft.graph.security.action | The type of action. The possible values are: `disable`, `enable`, `forcePasswordReset`, `revokeAllSessions`, `requireUserToSignInAgain`, `markUserAsCompromised`, `unknownFutureValue`. |
| correlationId | String | The unique identifier for tracking the request. |
| identityProvider | microsoft.graph.security.identityProvider | The identity provider type. The possible values are: `entraID`, `activeDirectory`, `okta`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.invokeActionResult",
  "accountId": "String",
  "action": "String",
  "identityProvider": "String",
  "correlationId": "String"
}
```
