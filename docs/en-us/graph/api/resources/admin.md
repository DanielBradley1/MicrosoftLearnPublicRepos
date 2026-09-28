<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/admin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# admin resource type

Namespace: microsoft.graph

Represents an entity that acts as a container for administrator functionality.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| configurationManagement | [configurationManagement](https://learn.microsoft.com/en-us/graph/api/resources/configurationmanagement?view=graph-rest-1.0) | A container for Tenant Configuration Management \(TCM\) resources. Read-only. |
| edge | [edge](https://learn.microsoft.com/en-us/graph/api/resources/edge?view=graph-rest-1.0) | A container for Microsoft Edge resources. Read-only. |
| exchange | [exchangeAdmin](https://learn.microsoft.com/en-us/graph/api/resources/exchangeadmin?view=graph-rest-1.0) | A container for the Exchange admin functionality. Read-only. |
| microsoft365Apps | [adminMicrosoft365Apps](https://learn.microsoft.com/en-us/graph/api/resources/adminmicrosoft365apps?view=graph-rest-1.0) | A container for the Microsoft 365 apps admin functionality. |
| people | [peopleAdminSettings](https://learn.microsoft.com/en-us/graph/api/resources/peopleadminsettings?view=graph-rest-1.0) | Represents a setting to control people-related admin settings in the tenant. |
| reportSettings | [adminReportSettings](https://learn.microsoft.com/en-us/graph/api/resources/adminreportsettings?view=graph-rest-1.0) | A container for administrative resources to manage reports. |
| serviceAnnouncement | [serviceAnnouncement](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncement?view=graph-rest-1.0) | A container for service communications resources. Read-only. |
| sharepointSettings | [sharepointSettings](https://learn.microsoft.com/en-us/graph/api/resources/sharepointsettings?view=graph-rest-1.0) | A container for administrative resources to manage tenant-level settings for SharePoint and OneDrive. |
| teams | [microsoft.graph.teamsAdministration.teamsAdminRoot](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamsadminroot?view=graph-rest-1.0) | A container for Teams administration functionalities, such as Teams telephone number management functionalities, user Teams configurations, and policy assignments. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.admin"
}
```
