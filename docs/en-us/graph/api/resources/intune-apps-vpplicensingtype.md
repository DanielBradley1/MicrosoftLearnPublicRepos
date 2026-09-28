<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-vpplicensingtype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# vppLicensingType resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for iOS Volume-Purchased Program \(Vpp\) Licensing Type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| supportsUserLicensing | Boolean | Whether the program supports the user licensing type. |
| supportsDeviceLicensing | Boolean | Whether the program supports the device licensing type. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.vppLicensingType",
  "supportsUserLicensing": true,
  "supportsDeviceLicensing": true
}
```
