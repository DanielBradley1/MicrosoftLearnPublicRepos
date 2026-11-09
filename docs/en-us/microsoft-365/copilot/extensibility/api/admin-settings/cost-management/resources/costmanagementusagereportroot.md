<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementusagereportroot -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# costManagementUsageReportRoot resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

The Copilot Cost Management usage reporting root, contained by [costManagementRoot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementroot) at `/copilot/costManagement/usageReports`. It's the containment parent for the usage report collections, which report consumption of Copilot Credits by user, security group, governed service, and funding class, and for raw per-user usage detail. Every usage report requires a time selector query parameter. For details, see [Usage report time selectors and paging](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/overview#usage-report-time-selectors-and-paging).

Note

The root itself isn't readable. `GET /copilot/costManagement/usageReports` returns a `404` response and carries no data. Use the contained collections instead.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List user usage records](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagerecord-list) | [costManagementUserUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagerecord) collection | Get reported consumption per user for one completed UTC day. |
| [List group usage records](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementgroupusagerecord-list) | [costManagementGroupUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementgroupusagerecord) collection | Get reported consumption per security group for one completed UTC day. |
| [List service usage records](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementserviceusagerecord-list) | [costManagementServiceUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementserviceusagerecord) collection | Get reported consumption per governed service for one completed UTC day. |
| [List funding usage records](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementfundingusagerecord-list) | [costManagementFundingUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementfundingusagerecord) collection | Get reported consumption per funding class for a calendar month. |
| [Get user usage detail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagedetail-get) | [costManagementUserUsageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagedetail) | Get one user's raw usage detail over a timestamp window. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity). Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `fundingUsageRecords` | [costManagementFundingUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementfundingusagerecord) collection | Reported consumption per funding class for a calendar month. |
| `groupUsageRecords` | [costManagementGroupUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementgroupusagerecord) collection | Reported consumption per security group for one completed UTC day. |
| `serviceUsageRecords` | [costManagementServiceUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementserviceusagerecord) collection | Reported consumption per governed service for one completed UTC day. |
| `userUsageDetails` | [costManagementUserUsageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagedetail) collection | Raw per-user usage detail, read one user at a time. The collection isn't listable; read by key only. |
| `userUsageRecords` | [costManagementUserUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagerecord) collection | Reported consumption per user for one completed UTC day, ranked by consumption. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementUsageReportRoot",
  "id": "String"
}
```
