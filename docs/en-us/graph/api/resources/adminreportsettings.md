<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/adminreportsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# adminReportSettings resource type

Namespace: microsoft.graph

Represents the tenant-level settings for Microsoft 365 reports.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/adminreportsettings-get?view=graph-rest-1.0) | [adminReportSettings](https://learn.microsoft.com/en-us/graph/api/resources/adminreportsettings?view=graph-rest-1.0) | Get the tenant-level settings for Microsoft 365 reports. |
| [Update](https://learn.microsoft.com/en-us/graph/api/adminreportsettings-update?view=graph-rest-1.0) | [adminReportSettings](https://learn.microsoft.com/en-us/graph/api/resources/adminreportsettings?view=graph-rest-1.0) | Update tenant-level settings for Microsoft 365 reports. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| displayConcealedNames | Boolean | If set to `true`, all reports conceal user information such as usernames, groups, and sites. If `false`, all reports show identifiable information. This property represents a setting in the Microsoft 365 admin center. Required. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.adminReportSettings",
  "displayConcealedNames": "Boolean"
}
```
