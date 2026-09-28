<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementcachedreportconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementCachedReportConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity representing the configuration of a cached report.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementCachedReportConfigurations](https://learn.microsoft.com/en-us/graph/api/api/intune-reporting-devicemanagementcachedreportconfiguration-list.md?view=graph-rest-1.0) | [deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementcachedreportconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementcachedreportconfiguration?view=graph-rest-1.0) objects. |
| [Get deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/api/intune-reporting-devicemanagementcachedreportconfiguration-get.md?view=graph-rest-1.0) | [deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementcachedreportconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementcachedreportconfiguration?view=graph-rest-1.0) object. |
| [Create deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/api/intune-reporting-devicemanagementcachedreportconfiguration-create.md?view=graph-rest-1.0) | [deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementcachedreportconfiguration?view=graph-rest-1.0) | Create a new [deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementcachedreportconfiguration?view=graph-rest-1.0) object. |
| [Delete deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/api/intune-reporting-devicemanagementcachedreportconfiguration-delete.md?view=graph-rest-1.0) | None | Deletes a [deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementcachedreportconfiguration?view=graph-rest-1.0). |
| [Update deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/api/intune-reporting-devicemanagementcachedreportconfiguration-update.md?view=graph-rest-1.0) | [deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementcachedreportconfiguration?view=graph-rest-1.0) | Update the properties of a [deviceManagementCachedReportConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementcachedreportconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for this entity. |
| reportName | String | Name of the report. |
| filter | String | Filters applied on report creation. |
| select | String collection | Columns selected from the report. |
| orderBy | String collection | Ordering of columns in the report. |
| metadata | String | Caller-managed metadata associated with the report. |
| status | [deviceManagementReportStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportstatus?view=graph-rest-1.0) | Status of the cached report. The possible values are: `unknown`, `notStarted`, `inProgress`, `completed`, `failed`. |
| lastRefreshDateTime | DateTimeOffset | Time that the cached report was last refreshed. |
| expirationDateTime | DateTimeOffset | Time that the cached report expires. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementCachedReportConfiguration",
  "id": "String (identifier)",
  "reportName": "String",
  "filter": "String",
  "select": [
    "String"
  ],
  "orderBy": [
    "String"
  ],
  "metadata": "String",
  "status": "String",
  "lastRefreshDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)"
}
```
