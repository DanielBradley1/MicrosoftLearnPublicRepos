<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityuserflow?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# identityUserFlow resource type

Namespace: microsoft.graph

User Flows enable you to define predefined, configurable policies for sign-in, sign-up, combined sign-up and sign-in, password reset, and profile update. This is a base class that other user flows inherit from.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the user flow. The prefix of **B2C\_1\_** is added to the value that you provide. |
| userFlowType | userFlowType | The possible values are: `signUp`, `signIn`, `signUpOrSignIn`, `passwordReset`, `profileUpdate`, `resourceOwner`, `unknownFutureValue`. |
| userFlowTypeVersion | Single | This is the version of the user flow type. Each user flow type can have different possible versions such as 1, 1.1 or 2. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "userFlowType": "string",
  "userFlowTypeVersion": "Single"
}
```
