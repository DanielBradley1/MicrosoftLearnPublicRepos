<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingoccurrence?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationSettingOccurrence resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| minDeviceOccurrence | Int32 | Minimum times setting can be set on device. A MinDeviceOccurrence of 0 means setting is optional |
| maxDeviceOccurrence | Int32 | Maximum times setting can be set on device. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSettingOccurrence",
  "minDeviceOccurrence": 1024,
  "maxDeviceOccurrence": 1024
}
```
