<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/insightsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# insightSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a daily or monthly summary of all usage insights on apps registered in your tenant that is configured for Microsoft Entra External ID for customers. A user \(in **activeUsers**\) can be counted more that once if they use multiple device platforms.

This resource represents a summary of the insights. For a breakdown of each insight, see the following resources and their associated APIs:

- [activeUsers](https://learn.microsoft.com/en-us/graph/api/resources/activeusersmetric?view=graph-rest-beta)
- [authentications](https://learn.microsoft.com/en-us/graph/api/resources/authenticationsmetric?view=graph-rest-beta)
- [mfaCompletion](https://learn.microsoft.com/en-us/graph/api/resources/mfacompletionmetric?view=graph-rest-beta)
- [userCountMetric](https://learn.microsoft.com/en-us/graph/api/resources/usercountmetric?view=graph-rest-beta)
- [userRequests](https://learn.microsoft.com/en-us/graph/api/resources/userrequestsmetric?view=graph-rest-beta)
- [userSignUp](https://learn.microsoft.com/en-us/graph/api/resources/usersignupmetric?view=graph-rest-beta)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List daily](https://learn.microsoft.com/en-us/graph/api/dailyuserinsightmetricsroot-list-summary?view=graph-rest-beta) | [insightSummary](https://learn.microsoft.com/en-us/graph/api/resources/insightsummary?view=graph-rest-beta) collection | Get a list of daily [insightSummary](https://learn.microsoft.com/en-us/graph/api/resources/insightsummary?view=graph-rest-beta) objects on apps registered in your tenant configured for Microsoft Entra External ID for customers. |
| [List monthly](https://learn.microsoft.com/en-us/graph/api/monthlyuserinsightmetricsroot-list-summary?view=graph-rest-beta) | [insightSummary](https://learn.microsoft.com/en-us/graph/api/resources/insightsummary?view=graph-rest-beta) collection | Get a list of monthly [insightSummary](https://learn.microsoft.com/en-us/graph/api/resources/insightsummary?view=graph-rest-beta) objects on apps registered in your tenant configured for Microsoft Entra External ID for customers. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeUsers | Int64 | Daily active users. |
| appId | String | The ID of the Microsoft Entra application. |
| authenticationCompletions | Int64 | Daily authentication completions. |
| authenticationRequests | Int64 | Daily authentication requests. |
| factDate | Date | The date of the insight. |
| id | String | Identifier for the insight. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| os | String | The platform for the device that the customers used. Supports `$filter` \(`eq`\). |
| securityTextCompletions | Int64 | Daily MFA SMS completions. |
| securityTextRequests | Int64 | Daily MFA SMS requests. |
| securityVoiceCompletions | Int64 | Daily MFA Voice completions. |
| securityVoiceRequests | Int64 | Daily MFA Voice requests. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.insightSummary",
  "activeUsers": "Int64",
  "appId": "String",
  "authenticationCompletions": "Int64",
  "authenticationRequests": "Int64",
  "factDate": "String (date)",
  "id": "String (identifier)",
  "os": "String",
  "securityTextCompletions": "Int64",
  "securityTextRequests": "Int64",
  "securityVoiceCompletions": "Int64",
  "securityVoiceRequests": "Int64"
}
```
