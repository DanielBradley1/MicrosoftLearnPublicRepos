<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mfacompletionmetric?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# mfaCompletionMetric resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents insights on the MFA usage for apps registered in your tenant configured for Microsoft Entra External ID for customers, over a specific period \(daily or monthly\).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List daily](https://learn.microsoft.com/en-us/graph/api/dailyuserinsightmetricsroot-list-mfacompletions?view=graph-rest-beta) | [mfaCompletionMetric](https://learn.microsoft.com/en-us/graph/api/resources/mfacompletionmetric?view=graph-rest-beta) collection | Get a list of daily [MFA completions](https://learn.microsoft.com/en-us/graph/api/resources/mfacompletionmetric?view=graph-rest-beta) on apps registered in your tenant configured for Microsoft Entra External ID for customers. |
| [List monthly](https://learn.microsoft.com/en-us/graph/api/monthlyuserinsightmetricsroot-list-mfacompletions?view=graph-rest-beta) | [mfaCompletionMetric](https://learn.microsoft.com/en-us/graph/api/resources/mfacompletionmetric?view=graph-rest-beta) collection | Get a list of monthly [MFA completions](https://learn.microsoft.com/en-us/graph/api/resources/mfacompletionmetric?view=graph-rest-beta) on apps registered in your tenant configured for Microsoft Entra External ID for customers. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The ID of the Microsoft Entra application. Supports `$filter` \(`eq`\). |
| attemptsCount | Int64 | Number of users who attempted to sign up. Supports `$filter` \(`eq`\). |
| factDate | Date | The date of the user insight. |
| id | String | Identifier for the user insight. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| mfaMethod | String | The MFA authentication method used by the customers. Supports `$filter` \(`eq`\). |
| os | String | The platform of the device that the customers used. Supports `$filter` \(`eq`\). |
| successCount | Int64 | Number of users who signed up successfully. Supports `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mfaCompletionMetric",
  "appId": "String",
  "attemptsCount": "Int64",
  "factDate": "String (date)",
  "id": "String (identifier)",
  "mfaMethod": "String",
  "os": "String",
  "successCount": "Int64"
}
```
