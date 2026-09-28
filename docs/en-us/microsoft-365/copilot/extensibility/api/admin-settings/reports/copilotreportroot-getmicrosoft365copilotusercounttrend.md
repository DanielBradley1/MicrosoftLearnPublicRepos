<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/reports/copilotreportroot-getmicrosoft365copilotusercounttrend -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# copilotReportRoot: getMicrosoft365CopilotUserCountTrend

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Get the trend in the daily number of active and enabled users of Microsoft 365 Copilot for a specified time period.

For more information about report views and names, see [Microsoft 365 reports - Microsoft 365 Copilot usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-usage). Copilot usage reports APIs are available as standard REST APIs under the Microsoft Graph namespace. For more information, see [Microsoft 365 Copilot APIs overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-overview).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Reports.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Reports.Read.All | Not available. |

Important

For delegated permissions to allow apps to read service usage reports on behalf of a user, the tenant administrator must have assigned the user one of the following Microsoft Entra ID limited administrator roles:

- Company Administrator
- AI Administrator
- Exchange Administrator
- SharePoint Administrator
- Lync Administrator
- Teams Service Administrator
- Teams Communications Administrator
- Global Reader
- Usage Summary Reports Reader
- Reports Reader

For more information, see [Authorization for APIs to read Microsoft 365 usage reports](https://learn.microsoft.com/en-us/graph/reportroot-authorization).

## HTTP request

```http
GET https://graph.microsoft.com/v1.0/copilot/reports/getMicrosoft365CopilotUserCountTrend(period={period}, version={version})
```

```http
GET https://graph.microsoft.com/beta/copilot/reports/getMicrosoft365CopilotUserCountTrend(period={period}, version={version})
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| --- | --- | --- |
| `period` | String | Required. The number of previous days over which to report aggregated usage. The supported values depend on the value of `version`. For `v1`, they are: `D7`, `D30`, `D90`, `D180`, `ALL`. For `v2`, they are `D7`, `D28`, `D90`, `D180`, `ALL`. The first four values follow the format `Dn` where `n` represents the number of previous days over which to aggregate data. `ALL` indicates to report usage for all supported periods \(7, 30, 90, and 180 days for `v1`, 7, 28, 90, and 180 days for `v2`\). |
| `version` | String | Optional. The requested report version. The supported value is `v2` \(default\). |

### Report versions

Version 1 reports contain the following information.

- Report Refresh Date
- Report Date
- Microsoft Teams Enabled Users
- Microsoft Teams Active Users
- Word Enabled Users
- Word Active Users
- PowerPoint Enabled Users
- PowerPoint Active Users
- Outlook Enabled Users
- Outlook Active Users
- Excel Enabled Users
- Excel Active Users
- OneNote Enabled Users
- OneNote Active Users
- Loop Enabled Users
- Loop Active Users
- Any App Enabled Users
- Any App Active Users
- Copilot Chat Enabled Users
- Copilot Chat Active Users
- Report Period

Version 2 reports contain all of the information from version 1, with the following additional information.

- Edge Enabled Users
- Edge Active Users
- Microsoft 365 Copilot Enabled Users
- Microsoft 365 Copilot Active Users
- Copilot Chat \(work\) Enabled Users
- Copilot Chat \(work\) Active Users
- Copilot Chat \(web\) Enabled Users
- Copilot Chat \(web\) Active Users
- Prompts submitted

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a Stream in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/reports/getMicrosoft365CopilotUserCountTrend(period='D7')
```

```http
GET https://graph.microsoft.com/beta/copilot/reports/getMicrosoft365CopilotUserCountTrend(period='D7')
```

### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

Report Refresh Date,Report Date,Microsoft Teams Enabled Users,Microsoft Teams Active Users,Word Enabled Users,Word Active Users,PowerPoint Enabled Users,PowerPoint Active Users,Outlook Enabled Users,Outlook Active Users,Excel Enabled Users,Excel Active Users,OneNote Enabled Users,OneNote Active Users,Loop Enabled Users,Loop Active Users,Any App Enabled Users,Any App Active Users,Copilot Chat Enabled Users,Copilot Chat Active Users,Report Period
2026-07-03,2026-07-03,25,0,25,0,25,0,25,0,25,0,25,0,25,0,25,0,25,0,7
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "reportRefreshDate": "2025-08-20",
      "reportPeriod": 7,
      "adoptionByDate": [
        {
          "reportDate": "2025-08-20",
          "anyAppEnabledUsers": 357584,
          "anyAppActiveUsers": 94745,
          "microsoftTeamsEnabledUsers": 357451,
          "microsoftTeamsActiveUsers": 72272,
          "wordEnabledUsers": 357451,
          "wordActiveUsers": 6602,
          "powerPointEnabledUsers": 357451,
          "powerPointActiveUsers": 2231,
          "outlookEnabledUsers": 357451,
          "outlookActiveUsers": 11786,
          "excelEnabledUsers": 357451,
          "excelActiveUsers": 1712,
          "oneNoteEnabledUsers": 357451,
          "oneNoteActiveUsers": 492,
          "loopEnabledUsers": 357451,
          "loopActiveUsers": 340,
          "copilotChatEnabledUsers": 357451,
          "copilotChatActiveUsers": 26609
        }
      ]
    }
  ]
}
```
