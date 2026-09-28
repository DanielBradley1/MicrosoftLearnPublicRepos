<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreports?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# deviceManagementReports resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Singleton entity that acts as a container for all reports functionality.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-get?view=graph-rest-1.0) | [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreports?view=graph-rest-1.0) | Read properties and relationships of the [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreports?view=graph-rest-1.0) object. |
| [Update deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-update?view=graph-rest-1.0) | [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreports?view=graph-rest-1.0) | Update the properties of a [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreports?view=graph-rest-1.0) object. |
| [getDeviceNonComplianceReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getdevicenoncompliancereport?view=graph-rest-1.0) | Stream |  |
| [getNoncompliantDevicesAndSettingsReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getnoncompliantdevicesandsettingsreport?view=graph-rest-1.0) | Stream |  |
| [getDevicesWithoutCompliancePolicyReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getdeviceswithoutcompliancepolicyreport?view=graph-rest-1.0) | Stream |  |
| [getPolicyNonComplianceReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getpolicynoncompliancereport?view=graph-rest-1.0) | Stream |  |
| [getPolicyNonComplianceMetadata action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getpolicynoncompliancemetadata?view=graph-rest-1.0) | Stream |  |
| [getPolicyNonComplianceSummaryReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getpolicynoncompliancesummaryreport?view=graph-rest-1.0) | Stream |  |
| [getSettingNonComplianceReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getsettingnoncompliancereport?view=graph-rest-1.0) | Stream |  |
| [getReportFilters action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getreportfilters?view=graph-rest-1.0) | Stream |  |
| [getConfigurationPolicyNonComplianceSummaryReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getconfigurationpolicynoncompliancesummaryreport?view=graph-rest-1.0) | Stream |  |
| [getConfigurationPolicyNonComplianceReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getconfigurationpolicynoncompliancereport?view=graph-rest-1.0) | Stream |  |
| [getConfigurationSettingNonComplianceReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getconfigurationsettingnoncompliancereport?view=graph-rest-1.0) | Stream |  |
| [getDeviceManagementIntentSettingsReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getdevicemanagementintentsettingsreport?view=graph-rest-1.0) | Stream |  |
| [getDeviceManagementIntentPerSettingContributingProfiles action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getdevicemanagementintentpersettingcontributingprofiles?view=graph-rest-1.0) | Stream |  |
| [getCompliancePolicyNonComplianceSummaryReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getcompliancepolicynoncompliancesummaryreport?view=graph-rest-1.0) | Stream |  |
| [getCompliancePolicyNonComplianceReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getcompliancepolicynoncompliancereport?view=graph-rest-1.0) | Stream |  |
| [getComplianceSettingNonComplianceReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getcompliancesettingnoncompliancereport?view=graph-rest-1.0) | Stream |  |
| [getCachedReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-getcachedreport?view=graph-rest-1.0) | Stream |  |
| [getHistoricalReport action](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreports-gethistoricalreport?view=graph-rest-1.0) | Stream |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for this entity. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| exportJobs | [deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjob?view=graph-rest-1.0) collection | Entity representing a job to export a report. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementReports",
  "id": "String (identifier)"
}
```
