<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# authenticationDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides the authentication details for a user sign-in, such as multifactor authentication \(MFA\) information and PTA/PHS details. This object is configured in the **authenticationDetails** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationMethod | String | The type of authentication method used to perform this step of authentication. Possible values: `Password`, `SMS`, `Voice`, `Authenticator App`, `Software OATH token`, `Satisfied by token`, `Previously satisfied`. |
| authenticationMethodDetail | String | Details about the authentication method used to perform this authentication step. For example, phone number \(for SMS and voice\), device name \(for Authenticator app\), and password source \(for example, cloud, AD FS, PTA, PHS\). |
| authenticationStepDateTime | DateTimeOffset | Represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| authenticationStepRequirement | String | The step of authentication that this satisfied. For example, primary authentication, or multifactor authentication. |
| authenticationStepResultDetail | String | Details about why the step succeeded or failed. For examples, user is blocked, fraud code entered, no phone input - timed out, phone unreachable, or claim in token. |
| succeeded | Boolean | Indicates the status of the authentication step. Possible values: `succeeded`, `failed`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "authenticationMethod": "String",
  "authenticationMethodDetail": "String",
  "authenticationStepDateTime": "String (timestamp)",
  "authenticationStepRequirement": "String",
  "authenticationStepResultDetail": "String",
  "succeeded": true
}
```
