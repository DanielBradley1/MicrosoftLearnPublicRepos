<!-- Source: https://learn.microsoft.com/en-us/graph/microsoft-graph-activity-logs-overview -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# Access Microsoft Graph activity logs

**Microsoft Graph activity logs** provide an audit trail of all HTTP requests that the Microsoft Graph service receives and processes for a tenant. Tenant admins can turn on log collection and set up downstream destinations by using diagnostic settings in Azure Monitor. The logs go to Log Analytics for analysis. You can export them to Azure Storage for long-term storage, or stream them with Azure Event Hubs to external SIEM tools for alerting, analysis, or archiving.

You get logs for API requests from line-of-business apps, API clients, SDKs, AI Clients querying the [Microsoft MCP Server for Enterprise](https://learn.microsoft.com/en-us/graph/mcp-server/overview), and Microsoft apps like Outlook, Microsoft Teams, or the Microsoft admin portals.

This service is available in these [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Prerequisites

To use Microsoft Graph activity logs, you need the following privileges.

- A Microsoft Entra ID P1 or P2 tenant license.
- An admin with a supported [Microsoft Entra administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). *Security Administrator* is the only least privileged admin role supported for setting up diagnostic settings.
- An Azure subscription with one of the following log destinations set up, and permissions to use data in the corresponding log destinations.

  - An Azure Log Analytics workspace to send logs to Azure Monitor
  - An Azure Storage account where you have List Keys permissions
  - An Azure Event Hubs namespace to connect with third-party solutions

## What data is available in the Microsoft Graph activity logs

This article shows the data about API requests that's available for Microsoft Graph activity logs in the Logs Analytics interface.

Tip

Requests to the [Microsoft MCP Server for Enterprise](https://learn.microsoft.com/en-us/graph/mcp-server/overview) have a **RequestUri** that includes `/enterprise`.

Warning

Don't store secrets or other sensitive information—such as passwords, credentials, access or refresh tokens, or connection strings—in directory object attributes or any other auditable resource exposed by Microsoft Graph. Microsoft Graph activity logs, along with other audit and sign-in logs, capture details about API requests, including request URIs. Any sensitive value that's passed in a request or stored on such a resource can be recorded in these logs, where it's readable by tenant administrators and by any downstream Log Analytics workspace, Azure Storage account, or SIEM system to which the logs are exported. Directory object attributes aren't a secure store for secrets; use a dedicated secret store such as [Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/overview) instead.

| Column | Type | Description |
| --- | --- | --- |
| AadTenantId | string | The Azure AD tenant ID. |
| ApiVersion | string | The API version of the event. |
| AppId | string | The identifier for the application. |
| ATContent | string | Reserved for future use. |
| ATContentH | string | Reserved for future use. |
| ATContentP | string | Reserved for future use. |
| \_BilledSize | real | The record size in bytes |
| ClientAuthMethod | int | Indicates how the client was authenticated. For a public client, the value is 0. If client ID and client secret are used, the value is 1. If a client certificate was used for authentication, the value is 2. |
| ClientRequestId | string | Optional. The client request identifier when sent. If no client request identifier is sent, the value will be equal to the operation identifier. |
| DeviceId | string | The identifier of the device from which the authentication request originated. |
| DurationMs | int | The duration of the request in milliseconds. |
| IdentityProvider | string | The identity provider that authenticated the subject of the token. |
| IPAddress | string | The IP address of the client from where the request occurred. |
| \_IsBillable | string | Specifies whether ingesting the data is billable. When \_IsBillable is `false` ingestion isn't billed to your Azure account |
| Location | string | The name of the region that served the request. |
| OperationId | string | The identifier for the batch. For non-batched requests, this will be unique per request. For batched requests, this will be the same for all requests in the batch. |
| RequestId | string | The identifier representing the request. |
| RequestMethod | string | The HTTP method of the event. |
| RequestUri | string | The URI of the request. |
| ResponseSizeBytes | int | The size of the response in Bytes. |
| ResponseStatusCode | int | The HTTP response status code for the event. |
| Roles | string | The roles in token claims. |
| Scopes | string | The scopes in token claims. |
| ServicePrincipalId | string | The identifier of the servicePrincipal making the request. |
| SessionId | string | The unique identifier for the authentication session. |
| SignInActivityId | string | The identifier representing the sign-in activitys. |
| SourceSystem | string | The type of agent the event was collected by. For example, `OpsManager` for Windows agent, either direct connect or Operations Manager, `Linux` for all Linux agents, or `Azure` for Azure Diagnostics |
| TenantId | string | The Log Analytics workspace ID |
| TimeGenerated | datetime | The date and time the request was received. |
| TokenIssuedAt | datetime | The timestamp the token was issued at. |
| Type | string | The name of the table |
| UniqueTokenId | string | The unique token identifier of the API call used to make the audited change. |
| UserAgent | string | The user agent information related to request. |
| UserId | string | The identifier of the user making the request. |
| Wids | string | Denotes the tenant-wide roles assigned to this user. |

## Common use cases for Microsoft Graph activity logs

- See all transactions made by applications and other API clients you've consented to in the tenant.
- Find activities that a compromised user account conducts in your tenant.
- Build detections and behavioral analysis to spot suspicious or unusual use of Microsoft Graph APIs.
- Investigate unexpected or suspicious privileged assignment of application permissions.
- Spot problematic or unexpected behaviors for client applications, like extreme call volumes.
- Monitor AI client interactions with Microsoft Graph APIs, including requests from AI applications and the [Microsoft MCP Server for Enterprise](https://learn.microsoft.com/en-us/graph/mcp-server/overview).
- Correlate Microsoft Graph requests made by a user or app with sign-in information.

## Set up Microsoft Graph activity logs

Stream logs through Diagnostic Setting in the Azure portal or by using Azure Resource Manager APIs. For more information, see the following articles:

- [Integrate activity logs with Azure Monitor logs](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
- [Configure diagnosticSettings through the Azure Resource Manager API](https://learn.microsoft.com/en-us/azure/templates/microsoft.insights/diagnosticsettings?pivots=deployment-language-arm-template)

Use the following articles to set up storage destinations:

- [Azure Log Analytics Workspace](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/tutorial-configure-log-analytics-workspace)
- [Azure Storage](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal)
- [Azure Event Hubs](https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-create)

## Cost planning estimates

If you already have a Microsoft Entra ID P1 license, you need an Azure subscription to set up the Log Analytics workspace, storage account, or Event Hubs. You get the Azure subscription at no cost, but you pay to use Azure resources.

The amount of data logged, and the cost incurred, can vary significantly depending on the tenant size and the applications in your tenant that interact with Microsoft Graph APIs. The following table gives estimates for log data size to help you calculate pricing. Use these estimates for general consideration only.

| Users in tenant | Storage \(GiB per month\) | Event Hubs messages \(per month\) | Azure Monitor Logs \(GiB per month\) |
| --- | --- | --- | --- |
| 1,000 | 14 | 62,000 | 15 |
| 100,000 | 1,000 | 4,800,000 | 1,200 |

See the following pricing details for each service:

- [Log Analytics pricing details](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/cost-logs#pricing-model)
- [Azure Storage pricing](https://azure.microsoft.com/pricing/details/storage/blobs)
- [Event Hubs pricing](https://azure.microsoft.com/pricing/details/event-hubs/)

## Cost reduction for Log Analytics

If you ingest the logs to a Log Analytics Workspace but are only interested in logs filtered by a criteria, such as omitting certain columns or rows, you can partially reduce costs by applying a workspace transformation on the Microsoft Graph Activity Logs table. To find out more about workspace transformations, how it affects ingestion costs, and how to apply a transformation to your Microsoft Graph Activity Logs, see [Data collection transformations in Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/data-collection-transformations).

An alternative approach to reduce Log Analytics cost is to switch to the Basic log data plan which lowers the bills by providing reduced capabilities. For more information, see [Set a table's log data plan to Basic or Analytics](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/basic-logs-configure).

## Azure Monitor Logs query examples

If you send Microsoft Graph activity logs to a Log Analytics workspace, you can query the logs using Kusto Query Language \(KQL\). For more information about queries in Log Analytics Workspace, see [Analyze Microsoft Entra activity logs with Log Analytics](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/howto-analyze-activity-logs-log-analytics). You can use these queries for data exploration, to build alert rules, build Azure dashboards, or integrate into your custom applications using the Azure Monitor Logs API or Query SDK.

The following Kusto query identifies the top 20 entities making requests to groups resources that are failing due to authorization:

```kusto
MicrosoftGraphActivityLogs
| where TimeGenerated >= ago(3d)
| where ResponseStatusCode == 401 or ResponseStatusCode == 403 
| where RequestUri contains "/groups"
| summarize UniqueRequests=count_distinct(RequestId) by AppId, ServicePrincipalId, UserId
| sort by UniqueRequests desc
| limit 20
```

The following Kusto query identifies resources queried or modified by potentially risky users:

```kusto
MicrosoftGraphActivityLogs
| where TimeGenerated > ago(30d)
| join AADRiskyUsers on $left.UserId == $right.Id
| extend resourcePath = replace_string(replace_string(replace_regex(tostring(parse_url(RequestUri).Path), @'(\/)+','/'),'v1.0/',''),'beta/','')
| summarize RequestCount=dcount(RequestId) by UserId, RiskState, resourcePath, RequestMethod, ResponseStatusCode
```

The following Kusto query allows you to correlate the Microsoft Graph activity logs and sign-in logs. Activity logs from Microsoft applications might not all have matching sign-in log entries. For more information, see [Sign-in logs known limitations](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/concept-sign-ins#known-limitations).

```kusto
MicrosoftGraphActivityLogs
| where TimeGenerated > ago(7d)
| join kind=leftouter (union SigninLogs, AADNonInteractiveUserSignInLogs, AADServicePrincipalSignInLogs, AADManagedIdentitySignInLogs, ADFSSignInLogs
    | where TimeGenerated > ago(7d))
    on $left.SignInActivityId == $right.UniqueTokenIdentifier
```

The following Kusto query identifies apps that are getting throttled:

```kusto
MicrosoftGraphActivityLogs 
| where TimeGenerated > ago(3d) 
| where ResponseStatusCode == 429 
| extend path = replace_string(replace_string(replace_regex(tostring(parse_url(RequestUri).Path), @'(\/)+','//'),'v1.0/',''),'beta/','') 
| extend UriSegments =  extract_all(@'\/([A-z2]+|\$batch)($|\/|\(|\$)',dynamic([1]),tolower(path)) 
| extend OperationResource = strcat_array(UriSegments,'/')| summarize RateLimitedCount=count() by AppId, OperationResource, RequestMethod 
| sort by RateLimitedCount desc 
| limit 100 
```

The following query allows you to render a time-series chart:

```kusto
MicrosoftGraphActivityLogs 
| where TimeGenerated  between (ago(3d) .. ago(1h))  
| summarize EventCount = count() by bin(TimeGenerated, 10m) 
| render timechart 
    with ( 
    title="Recent traffic patterns", 
    xtitle="Time", 
    ytitle="Requests", 
    legend=hidden 
    )
```

## Limitations

- The Microsoft Graph activity logs feature allows the tenant administrators to collect logs for the resource tenant. This feature doesn't allow you to see the activities of a multitenant application in another tenant.
- You can't filter Microsoft Graph activity logs through diagnostic settings in Azure Monitor. However, options are available to reduce costs in Azure Log Analytics Workspace. For more information, see [Workspace transformation](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/tutorial-workspace-transformations-portal).
- In most regions, the events are available and delivered to the configuration destination within 30 minutes. In less common cases, some events might take up to 2 hours to be delivered to the destination.

## Related content

- [Azure Monitor Reference: MicrosoftGraphActivityLogs](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/microsoftgraphactivitylogs)
- [Stream data from Azure Monitor to an event hub or external partner](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/stream-monitoring-data-event-hubs)
