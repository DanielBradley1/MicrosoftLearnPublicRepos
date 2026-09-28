<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-chromeosdeviceproperty?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# chromeOSDeviceProperty resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents a property of the ChromeOS device.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name of the property |
| value | String | Value of the property |
| valueType | String | Type of the value |
| updatable | Boolean | Whether this property is updatable |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.chromeOSDeviceProperty",
  "name": "String",
  "value": "String",
  "valueType": "String",
  "updatable": true
}
```
