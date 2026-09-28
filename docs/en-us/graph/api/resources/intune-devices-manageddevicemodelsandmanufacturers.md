<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicemodelsandmanufacturers?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedDeviceModelsAndManufacturers resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Models and Manufactures meatadata for managed devices in the account

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceModels | String collection | List of Models for managed devices in the account |
| deviceManufacturers | String collection | List of Manufactures for managed devices in the account |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDeviceModelsAndManufacturers",
  "deviceModels": [
    "String"
  ],
  "deviceManufacturers": [
    "String"
  ]
}
```
