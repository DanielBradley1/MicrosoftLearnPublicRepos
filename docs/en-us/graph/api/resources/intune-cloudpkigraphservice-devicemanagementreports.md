<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-cloudpkigraphservice-devicemanagementreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementReports resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Singleton entity that acts as a container for reporting functionality.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/intune-cloudpkigraphservice-devicemanagementreports-get?view=graph-rest-beta) | [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-cloudpkigraphservice-devicemanagementreports?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-cloudpkigraphservice-devicemanagementreports?view=graph-rest-beta) object. |
| [Update deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/intune-cloudpkigraphservice-devicemanagementreports-update?view=graph-rest-beta) | [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-cloudpkigraphservice-devicemanagementreports?view=graph-rest-beta) | Update the properties of a [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-cloudpkigraphservice-devicemanagementreports?view=graph-rest-beta) object. |
| [retrieveCloudPkiLeafCertificateReport action](https://learn.microsoft.com/en-us/graph/api/intune-cloudpkigraphservice-devicemanagementreports-retrievecloudpkileafcertificatereport?view=graph-rest-beta) | Stream |  |
| [retrieveCloudPkiLeafCertificateSummaryReport action](https://learn.microsoft.com/en-us/graph/api/intune-cloudpkigraphservice-devicemanagementreports-retrievecloudpkileafcertificatesummaryreport?view=graph-rest-beta) | Stream |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Required Graph property |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementReports",
  "id": "String (identifier)"
}
```
