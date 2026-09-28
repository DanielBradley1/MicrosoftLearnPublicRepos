<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/reports/resources/copilotreportroot -->
<!-- Sitemap-Last-Modified: 2026-01-10 -->

# copilotReportRoot resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a container for Microsoft 365 Copilot usage reporting resources.

For more information about report views and names, see [Microsoft 365 reports - Microsoft 365 Copilot usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-usage). Copilot usage reports APIs are available as standard REST APIs under the Microsoft Graph namespace. For more information, see [Microsoft 365 Copilot APIs overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-overview).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [getMicrosoft365CopilotUserCountSummary](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/reports/copilotreportroot-getmicrosoft365copilotusercountsummary) | Stream | Get the aggregated number of active and enabled users of Microsoft 365 Copilot for a specified time period. |
| [getMicrosoft365CopilotUserCountTrend](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/reports/copilotreportroot-getmicrosoft365copilotusercounttrend) | Stream | Get the trend in the daily number of active and enabled users of Microsoft 365 Copilot for a specified time period. |
| [getMicrosoft365CopilotUsageUserDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/reports/copilotreportroot-getmicrosoft365copilotusageuserdetail) | Stream | Get the most recent activity data for enabled users of Microsoft 365 Copilot apps. |

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotReportRoot"
}
```
