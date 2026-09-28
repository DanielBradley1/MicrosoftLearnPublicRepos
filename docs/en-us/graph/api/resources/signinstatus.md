<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signinstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# signInStatus resource type

Namespace: microsoft.graph

Provides the sign-in status \(Success or Failure\) of the sign-in. This object is configured in the **status** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalDetails | String | Provides additional details on the sign-in activity |
| errorCode | Int32 | Provides the 5-6 digit error code that's generated during a sign-in failure. Check out the [list of error codes and messages](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-troubleshoot-sign-in-errors#sign-in-error-codes). |
| failureReason | String | Provides the error message or the reason for failure for the corresponding sign-in activity. Check out the [list of error codes and messages](https://learn.microsoft.com/en-us/azure/active-directory/active-directory-reporting-activity-sign-ins-errors). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "additionalDetails": "String",
  "errorCode": 1024,
  "failureReason": "String"
}
```
