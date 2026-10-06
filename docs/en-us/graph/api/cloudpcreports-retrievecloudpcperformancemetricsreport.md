<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecloudpcperformancemetricsreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# cloudPcReports: retrieveCloudPcPerformanceMetricsReport

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get VM-level utilization and performance metrics for a specific Cloud PC from the [cloudPcReports](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreports?view=graph-rest-beta) resource, including CPU, memory, and network metrics. The metrics are returned as flattened time-series data.

This API supports only Windows 365 Enterprise Cloud PCs and Windows 365 Frontline Cloud PCs in dedicated mode.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.Read.All | CloudPC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.Read.All | CloudPC.ReadWrite.All |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/reports/retrieveCloudPcPerformanceMetricsReport
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| cloudPcId | String | The unique identifier \(GUID\) of the target Cloud PC. Required. |
| metricNames | [cloudPcPerformanceMetricNamesType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreports?view=graph-rest-beta#cloudpcperformancemetricnamestype-values) | Specifies which VM-level performance metrics to retrieve. This flagged enumeration allows multiple members to be selected simultaneously. The possible values are: `cpuUsageInPercentage`, `availableMemoryInPercentage`, `networkInboundInBytes`, `networkOutboundInBytes`, `inboundFlowsCount`, `outboundFlowsCount`, `unknownFutureValue`. Required. |
| endDateTime | DateTimeOffset | The ISO 8601 UTC end time. Use together with **startDateTime** to specify a custom window. Mutually exclusive with **timeRange**. If neither this pair nor **timeRange** is provided, the default **timeRange** of `last24Hours` is used. Optional. |
| startDateTime | DateTimeOffset | The ISO 8601 UTC start time. Use together with **endDateTime** to specify a custom window. Mutually exclusive with **timeRange**. If neither this pair nor **timeRange** is provided, the default **timeRange** of `last24Hours` is used. Optional. |
| timeRange | [cloudPcVmPerformanceMetricsTimeRange](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreports?view=graph-rest-beta#cloudpcvmperformancemetricstimerange-values) | A predefined time range. The possible values are: `last2Hours`, `last4Hours`, `last12Hours`, `last24Hours`, `last48Hours`, `last4Days`, `last7Days`, `last14Days`, `last28Days`, `unknownFutureValue`. Defaults to `last24Hours` when neither **timeRange** nor **startDateTime**/**endDateTime** is provided. Mutually exclusive with **startDateTime**/**endDateTime**. Optional. |

## Response

If successful, this action returns a `200 OK` response code and a Stream in the response body.

The stream contains a JSON object with a `value` array. Each element is one time-series data point for a single metric, and the same property shape is used for every metric returned.

| Property | Type | Description |
| :--- | :--- | :--- |
| metricsName | String | The metric name that this data point belongs to. Matches the camelCase member from [cloudPcPerformanceMetricNamesType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreports?view=graph-rest-beta#cloudpcperformancemetricnamestype-values), for example, `cpuUsageInPercentage` or `availableMemoryInPercentage`. |
| timeStamp | DateTimeOffset | The UTC start time of the aggregation interval for this data point. |
| average | Double | The average value of the metric over the interval. |
| minimum | Double | The minimum value observed in the interval. |
| maximum | Double | The maximum value observed in the interval. |
| total | Double | The sum of all sampled values in the interval. |
| count | Double | The number of samples aggregated into this data point. |

The unit of **average**, **minimum**, **maximum**, and **total** depends on the metric. For example, the unit is a percentage for `cpuUsageInPercentage` and bytes for `networkInboundInBytes`.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/retrieveCloudPcPerformanceMetricsReport
Content-Type: application/json

{
  "cloudPcId": "11111111-1111-1111-1111-111111111111",
  "metricNames": "cpuUsageInPercentage,availableMemoryInPercentage",
  "timeRange": "last24Hours"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

{
  "value": [
    {
      "metricsName": "cpuUsageInPercentage",
      "timeStamp": "2026-08-03T08:00:00Z",
      "average": 23.4,
      "minimum": 5.1,
      "maximum": 78.9,
      "total": 468.0,
      "count": 20.0
    },
    {
      "metricsName": "availableMemoryInPercentage",
      "timeStamp": "2026-08-03T08:00:00Z",
      "average": 61.2,
      "minimum": 40.5,
      "maximum": 82.3,
      "total": 1224.0,
      "count": 20.0
    }
  ]
}
```
