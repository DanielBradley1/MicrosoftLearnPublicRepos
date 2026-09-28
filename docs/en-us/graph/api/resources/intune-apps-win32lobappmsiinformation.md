<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappmsiinformation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# win32LobAppMsiInformation resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains MSI app properties for a Win32 App.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| productCode | String | The MSI product code. |
| productVersion | String | The MSI product version. |
| upgradeCode | String | The MSI upgrade code. |
| requiresReboot | Boolean | Whether the MSI app requires the machine to reboot to complete installation. |
| packageType | [win32LobAppMsiPackageType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappmsipackagetype?view=graph-rest-1.0) | The MSI package type. The possible values are: `perMachine`, `perUser`, `dualPurpose`. |
| productName | String | The MSI product name. |
| publisher | String | The MSI publisher. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppMsiInformation",
  "productCode": "String",
  "productVersion": "String",
  "upgradeCode": "String",
  "requiresReboot": true,
  "packageType": "String",
  "productName": "String",
  "publisher": "String"
}
```
