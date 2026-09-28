<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# cloudPcReports resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Windows 365 Cloud PC-related reports, including the Windows 365 Cloud PC remote connections report.

Use a method in the [Methods](#methods) section to get the corresponding report data in the response. Alternatively, you can use the [cloudPCExportJob](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexportjob?view=graph-rest-beta) resource and specify a storage account URL to download the specific report.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get action status reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getactionstatusreports?view=graph-rest-beta) | Stream | Get the remote action status reports, including data such as the Cloud PC ID, Cloud PC device display name, initiating user's principal name, device owner's user principal name, action taken, and action state. |
| [Get bulk action status reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievebulkactionstatusreport?view=graph-rest-beta) | Stream | Get the bulk remote action status reports, including data such as the bulk action ID, bulk action display name, initiating user's principal name, action type, and action state. |
| [Get Cloud PC troubleshooting reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecloudpctroubleshootreports?view=graph-rest-beta) | Stream | Get Cloud PC troubleshooting reports, including tenant-level, configuration, user and device, and view data table reports. |
| [Get frontline report](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getfrontlinereport?view=graph-rest-beta) | Stream | Get Frontline Cloud PC license usage reports, such as **servicePlanId**, **licenseCount**, and **claimedLicenseCount**, for real-time, 7 days, or 28 days trend. |
| [Get inaccessible Cloud PC reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getinaccessiblecloudpcreports?view=graph-rest-beta) | Stream | Get inaccessible Cloud PCs with details, including the latest health state, failed connection count, failed health check count, and system status. |
| [Get raw remote connection reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getrawremoteconnectionreports?view=graph-rest-beta) | Stream | Get the raw real-time remote connection report for a Cloud PC without any calculation or aggregation. |
| [Get real-time remote connection latency reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getrealtimeremoteconnectionlatency?view=graph-rest-beta) | Stream | Get the real-time remote connection latency reports like current round trip time and available bandwidth of a Cloud PC. |
| [Get real-time remote connection status reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getrealtimeremoteconnectionstatus?view=graph-rest-beta) | Stream | Get the real-time remote connection status reports like sign-in status or days since the last use of a Cloud PC. |
| [Get remote connection historical reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getremoteconnectionhistoricalreports?view=graph-rest-beta) | Stream | Get a Cloud PC's remote connection historical reports, such as **signInDateTime**, **signOutDateTime**, or **usageInHour**, in a given period. |
| [Get total aggregated remote connection reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-gettotalaggregatedremoteconnectionreports?view=graph-rest-beta) | Stream | Get the total aggregated remote connection reports, like usage and **daysSinceLastUse**, in a given period. |
| [Retrieve Cloud PC performance metrics report](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecloudpcperformancemetricsreport?view=graph-rest-beta) | Stream | Get VM-level utilization and performance metrics for a specific Cloud PC, including CPU, memory, and network metrics. |
| [Retrieve Cloud PC tenant metrics report](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecloudpctenantmetricsreport?view=graph-rest-beta) | Stream | Get a report related to the performance of Cloud PCs. |
| [Retrieve cross-region disaster recovery report](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecrossregiondisasterrecoveryreport?view=graph-rest-beta) | Stream | Retrieve the Windows 365 cross-region disaster recovery report, including cloudPcId, userId, deviceId, cloudPCDeviceDisplayName, userPrincipalName, enabledDRType, disasterRecoveryStatus, licenseType, drHealthStatus, currentRestorePointDateTime, backupCloudPcStatus, and activationExpirationDateTime. |
| [Retrieve connection quality reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrieveconnectionqualityreports?view=graph-rest-beta) | Stream | Get the overall connection quality reports for all devices in the current tenant, the regional connection quality trend report, and the regional connection quality insight report, including round trip time, available bandwidth, UPD usage, and dropped connections. |
| [Get daily aggregated remote connection reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getdailyaggregatedremoteconnectionreports?view=graph-rest-beta) | Stream | Get the daily aggregated remote connection reports like round trip time and available bandwidth in a given period. |
| [Get Cloud PC performance report \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getcloudpcperformancereport?view=graph-rest-beta) | Stream | Get a report related to the performance of Cloud PCs. This API is deprecated and stopped returning data on December 31, 2024. Going forward, use the [retrieveCloudPcTenantMetricsReport](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecloudpctenantmetricsreport?view=graph-rest-beta) API. |
| [Get Cloud PC recommendation reports \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getcloudpcrecommendationreports?view=graph-rest-beta) | Stream | Get the device recommendation reports for Cloud PCs, such as the usage category report. This API is deprecated and will stop returning data on July 01, 2025. Going forward, use the [retrieveCloudPcRecommendationReports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecloudpcrecommendationreports?view=graph-rest-beta) API. |
| [Get connection quality reports \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-gettotalaggregatedremoteconnectionreports?view=graph-rest-beta) | Stream | Get the overall connection quality reports for all devices within a current tenant during a given period, including metrics like the average round trip time \(P50\), average available bandwidth, and UDP connection percentage. Also get other real-time metrics such as last connection round trip time, last connection client IP, last connection gateway, and last connection protocol. This API is deprecated and stopped returning data on December 31, 2024. Going forward, use the [retrieveConnectionQualityReports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrieveconnectionqualityreports?view=graph-rest-beta) API. |
| [Get shared use license usage report \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getshareduselicenseusagereport?view=graph-rest-beta) | Stream | Get the shared use license usage reports, such as **servicePlanId**, **licenseCount**, and **claimedLicenseCount**, for real-time, 7 days, or 28 days trend. |
| [Retrieve Cloud PC recommendation reports \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecloudpcrecommendationreports?view=graph-rest-beta) | Stream | Get the device recommendation reports for Cloud PCs, such as the usage category report. This API is deprecated and will stop returning data on December 31, 2025. Going forward, use the [cloudPcReport: retrieveCloudPcRecommendationReports](https://learn.microsoft.com/en-us/graph/api/cloudpcreport-retrievecloudpcrecommendationreports?view=graph-rest-beta) API. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the reports. Read-only. |

### cloudPCPerformanceReportName values

| Member | Description |
| :--- | :--- |
| performanceTrendReport | Indicates a daily aggregated report that provides a list of connection quality metrics for Cloud PCs over the past seven days within a tenant. The metrics include `SlowRoundTripTimeCloudPcCount`, `LowUdpConnectionPercentageCount`, `NoTimeConnectedCloudPcCount`, and `LowTimeConnectedCloudPcCount`. Each daily report is an aggregation of the previous 28 days, counted back from the trigger time. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| cloudPcInsightReport | Indicates Cloud PC-level configuration data with insights. The `cloudPcInsightReport` member isn't currently implemented. Don't use. |

### cloudPCTroubleshootReportType values

| Member | Description |
| :--- | :--- |
| troubleshootTenantGlobalFilterReport | Indicates the global filter parameters for tenant-level troubleshoot reports. |
| troubleshootTenantNetworkTrendReport | Indicates time-series trend of network metrics at tenant level. |
| troubleshootTenantNetworkAggregatedReport | Indicates aggregated network metrics at tenant level. |
| troubleshootTenantConnectionFailureRateTrendReport | Indicates time-series trend of connection failure rate at tenant level. |
| troubleshootTenantConnectionFailureRateAggregatedReport | Indicates aggregated connection failure rate at tenant level. |
| troubleshootTenantCloudPCHealthTrendReport | Indicates time-series trend of Cloud PC health metrics at tenant level. |
| troubleshootTenantCloudPCHealthAggregatedReport | Indicates aggregated Cloud PC health metrics at tenant level. |
| troubleshootTenantActiveConnectionCountTrendReport | Indicates time-series trend of active connection count at tenant level. |
| troubleshootTenantActiveConnectionCountAggregatedReport | Indicates aggregated active connection count at tenant level. |
| troubleshootTenantMeanTimeToFailureTrendReport | Indicates time-series trend of Mean Time To Failure at tenant level. |
| troubleshootTenantMeanTimeToFailureAggregatedReport | Indicates aggregated Mean Time To Failure at tenant level. |
| troubleshootTenantRemoteSignInTimeTrendReport | Indicates time-series trend of remote sign-in time at tenant level. |
| troubleshootTenantRemoteSignInTimeAggregatedReport | Indicates aggregated remote sign-in time at tenant level. |
| troubleshootEventsOfViewDataTableReport | Indicates tabular view of troubleshoot events. |
| troubleshootTenantEnvironmentMetricsOfViewDataTableReport | Indicates tabular view of tenant-level environment metrics. |
| troubleshootCloudPCMetricsOfViewDataTableReport | Indicates tabular view of Cloud PC-level troubleshoot metrics. |
| troubleshootConfigurationConnectionCountTrendV1Report | Indicates time-series trend of connection count grouped by configuration. |
| troubleshootConfigurationTotalConnectionCountBarV1Report | Indicates total connection count distribution by configuration. |
| troubleshootConfigurationGlobalFilterV1Report | Indicates the global filter parameters for configuration-level troubleshoot reports. |
| troubleshootConnectionConfigurationOfViewDataTableV1Report | Indicates tabular view of connection configuration data. |
| troubleshootTenantConnectedDevicesOfViewDataTableReport | Indicates tabular view of connected devices at tenant level. |
| troubleshootEnvironmentOverviewOfViewDataTableReport | Indicates tabular view of environment overview metrics. |
| troubleshootCloudPCNetworkTrendReport | Indicates time-series trend of network metrics at Cloud PC level. |
| troubleshootCloudPCNetworkAggregatedReport | Indicates aggregated network metrics at Cloud PC level. |
| troubleshootCloudPCErrorTrendReport | Indicates time-series trend of connection errors at Cloud PC level. |
| troubleshootCloudPCErrorAggregatedReport | Indicates aggregated connection error metrics at Cloud PC level. |
| troubleshootCloudPCDurationTrendReport | Indicates time-series trend of connection duration at Cloud PC level. |
| troubleshootCloudPCDurationAggregatedReport | Indicates aggregated connection duration at Cloud PC level. |
| troubleshootCloudPCRemoteSignInTimeTrendReport | Indicates time-series trend of remote sign-in time at Cloud PC level. |
| troubleshootCloudPCRemoteSignInTimeAggregatedReport | Indicates aggregated remote sign-in time at Cloud PC level. |
| troubleshootCloudPCListReport | Indicates list report of Cloud PCs with troubleshoot details. |
| troubleshootCloudPCHealthTrendReport | Indicates time-series trend of health metrics at Cloud PC level. |
| troubleshootMatchedUserReport | Indicates report of users matched to specified troubleshoot criteria. |
| troubleshootMatchedCloudPCReport | Indicates report of Cloud PCs matched to specified troubleshoot criteria. |
| troubleshootUserListReport | Indicates list report of users with troubleshoot details. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### cloudPcPerformanceMetricNamesType values

| Member | Description |
| :--- | :--- |
| cpuUsageInPercentage | Indicates the percentage of allocated compute units in use by the Cloud PC \(0-100\). |
| availableMemoryInPercentage | Indicates the percentage of physical memory available to the guest OS \(0-100\). Lower values signal memory pressure. |
| networkInboundInBytes | Indicates the total bytes received across all network interfaces during the aggregation interval. |
| networkOutboundInBytes | Indicates the total bytes sent across all network interfaces during the aggregation interval. |
| inboundFlowsCount | Indicates the number of active inbound network flows. |
| outboundFlowsCount | Indicates the number of active outbound network flows. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### cloudPcVmPerformanceMetricsTimeRange values

| Member | Description |
| :--- | :--- |
| last2Hours | Indicates a time range of the last 2 hours. |
| last4Hours | Indicates a time range of the last 4 hours. |
| last12Hours | Indicates a time range of the last 12 hours. |
| last24Hours | Default. Indicates a time range of the last 24 hours. |
| last48Hours | Indicates a time range of the last 48 hours. |
| last4Days | Indicates a time range of the last 4 days. |
| last7Days | Indicates a time range of the last 7 days. |
| last14Days | Indicates a time range of the last 14 days. |
| last28Days | Indicates a time range of the last 28 days. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| exportJobs | [cloudPcExportJob](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexportjob?view=graph-rest-beta) collection | The export jobs created for downloading reports. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcReports",
  "id": "String (identifier)"
}
```
