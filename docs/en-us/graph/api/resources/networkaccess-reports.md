<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-reports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# reports resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A summary of access activity for a Global Secure Access service. For more information, see [What is application usage analytics](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-application-usage-analytics).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get application usage analytics](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getapplicationusageanalytics?view=graph-rest-beta) | [microsoft.graph.networkaccess.applicationAnalyticsUsagePoint](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-applicationanalyticsusagepoint?view=graph-rest-beta) collection | Get a collection of application usage analytics data points based on aggregated traffic logs for a specified time period. |
| [Get cloud application reports](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getcloudapplicationreport?view=graph-rest-beta) | [microsoft.graph.networkaccess.cloudApplicationReport](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudapplicationreport?view=graph-rest-beta) collection | Get a collection of cloud application reports based on aggregated traffic logs for a specified time period. |
| [Get connection summaries](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getconnectionsummaries?view=graph-rest-beta) | [microsoft.graph.networkaccess.getConnectionSummary](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connectionsummary?view=graph-rest-beta) collection | Get a collection of connections counts per traffic type, whether Private, Internet, or Microsoft.. |
| [Get cross-tenant access report](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-crosstenantaccessreport?view=graph-rest-beta) | [microsoft.graph.networkaccess.crossTenantAccess](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantaccess?view=graph-rest-beta) | A report of access from external IDs to the tenant through Microsoft Entra External ID.. |
| [Get cross-tenant access summary](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getcrosstenantsummary?view=graph-rest-beta) | [microsoft.graph.networkaccess.crossTenantSummary](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantsummary?view=graph-rest-beta) | A summary of cross-tenant access. |
| [Get destination report](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-destinationreport?view=graph-rest-beta) | [microsoft.graph.networkaccess.destination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-destination?view=graph-rest-beta) collection | A report about all outgoing network connections within a specified time frame. |
| [Get destination summary](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getdestinationsummaries?view=graph-rest-beta) | [microsoft.graph.networkaccess.destinationSummary](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-destinationsummary?view=graph-rest-beta) collection | A summary of destinations. |
| [Get device usage report](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-devicereport?view=graph-rest-beta) | [microsoft.graph.networkaccess.device](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-device?view=graph-rest-beta) | A detailed report of device network traffic. |
| [Get device usage summary](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getdeviceusagesummary?view=graph-rest-beta) | [microsoft.graph.networkaccess.deviceUsageSummary](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deviceusagesummary?view=graph-rest-beta) | A summary of device usage. |
| [Get discovered application segment report](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getdiscoveredapplicationsegmentreport?view=graph-rest-beta) | [microsoft.graph.networkaccess.discoveredApplicationSegmentReport](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-discoveredapplicationsegmentreport?view=graph-rest-beta) collection | Returns a collection of application segments detected in network traffic. |
| [Get enterprise application report](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getenterpriseapplicationreport?view=graph-rest-beta) | [microsoft.graph.networkaccess.enterpriseApplicationReport](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-enterpriseapplicationreport?view=graph-rest-beta) collection | Get a collection of enterprise application reports based on aggregated traffic logs for a specified time period in Global Secure Access. |
| [Get entities summary](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-entitiessummaries?view=graph-rest-beta) | [microsoft.graph.networkaccess.entitiesSummary](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-entitiessummary?view=graph-rest-beta) collection | A summary of unique connectivity entities. |
| [Get transaction summaries](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-transactionsummaries?view=graph-rest-beta) | [microsoft.graph.networkaccess.transactionSummary](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-transactionsummary?view=graph-rest-beta) collection | A summary of network transactions. |
| [Get usage profiling](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-usageprofiling?view=graph-rest-beta) | [microsoft.graph.networkaccess.usageProfilingPoint](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-usageprofilingpoint?view=graph-rest-beta) collection | Returns an object containing count tables for the traffic types in Global Secure Access, aggregated by the time period specified. |
| [Get user usage report](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-userreport?view=graph-rest-beta) | [microsoft.graph.networkaccess.user](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-user?view=graph-rest-beta) collection | A report of all users who had network traffic during a specified time period. |
| [Get web category report](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-webcategoryreport?view=graph-rest-beta) | [microsoft.graph.networkaccess.webCategoriesSummary](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategoriessummary?view=graph-rest-beta) collection | Get the number of users, devices, and transactions for destination URLs, grouped by web category. |

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.reports"
}
```
