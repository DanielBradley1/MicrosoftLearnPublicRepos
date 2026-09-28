<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-dataprocessorserviceforwindowsfeaturesonboarding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# dataProcessorServiceForWindowsFeaturesOnboarding resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A configuration entity for MEM features that utilize Data Processor Service for Windows \(DPSW\) data.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hasValidWindowsLicense | Boolean | Indicates whether the tenant has required Windows license. When TRUE, the tenant has the required Windows license. When FALSE, the tenant does not have the required Windows license. Default value is FALSE. |
| areDataProcessorServiceForWindowsFeaturesEnabled | Boolean | Indicates whether the tenant has enabled MEM features utilizing Data Processor Service for Windows \(DPSW\) data. When TRUE, the tenant has enabled MEM features utilizing Data Processor Service for Windows \(DPSW\) data. When FALSE, the tenant has not enabled MEM features utilizing Data Processor Service for Windows \(DPSW\) data. Default value is FALSE. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.dataProcessorServiceForWindowsFeaturesOnboarding",
  "hasValidWindowsLicense": true,
  "areDataProcessorServiceForWindowsFeaturesEnabled": true
}
```
