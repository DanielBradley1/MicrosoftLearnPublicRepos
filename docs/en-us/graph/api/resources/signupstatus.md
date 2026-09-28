<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signupstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# signUpStatus resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides the status \(success or failure\) of the sign-up step. This object is configured in the **status** property of [selfServiceSignUp](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignup?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalDetails | String | Provides additional details on the sign-up activity. |
| errorCode | Int32 | Provides the 5-6 digit error code that's generated during a sign-up failure. |
| failureReason | String | Provides the error message or the reason for failure for the corresponding sign-up activity. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "additionalDetails": "String",
  "errorCode": 1024,
  "failureReason": "String"
}
```
