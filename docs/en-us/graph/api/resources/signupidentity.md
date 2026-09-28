<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signupidentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# signUpIdentity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the identity of the user who initiated a sign-up. This object is configured in the **signUpIdentity** property of [selfServiceSignUp](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignup?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| signUpIdentifier | String | The identification that the user is trying to utilize to sign up. |
| signUpIdentifierType | signUpIdentifierType | The type of sign-up the user initiated. Possible values include: `emailAddress`, `unknownFutureValue`. Supports `$filter` \(`eq`\) on the `emailAddress`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "signUpIdentifier": "String",
  "signUpIdentifierType": "String"
}
```
