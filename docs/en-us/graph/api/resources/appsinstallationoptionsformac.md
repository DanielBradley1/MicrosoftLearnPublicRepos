<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appsinstallationoptionsformac?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# appsInstallationOptionsForMac resource type

Namespace: microsoft.graph

Represents the tenant-level Microsoft 365 applications installation options for a MAC platform. You can specify whether users can install Microsoft 365 apps on their own MAC devices. If admins choose not to allow it, they can manually deploy apps to users instead.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isMicrosoft365AppsEnabled | Boolean | Specifies whether users can install Microsoft 365 apps on their MAC devices. The default value is `true`. |
| isSkypeForBusinessEnabled | Boolean | Specifies whether users can install Skype for Business on their MAC devices running OS X El Capitan 10.11 or later. The default value is `true`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appsInstallationOptionsForMac",
  "isMicrosoft365AppsEnabled": "Boolean",
  "isSkypeForBusinessEnabled": "Boolean"
}
```
