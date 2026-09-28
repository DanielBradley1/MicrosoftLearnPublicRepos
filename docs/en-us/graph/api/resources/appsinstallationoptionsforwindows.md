<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appsinstallationoptionsforwindows?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# appsInstallationOptionsForWindows resource type

Namespace: microsoft.graph

Represents the tenant-level Microsoft 365 application installation options for a Windows platform. You can specify whether users can install Microsoft 365 apps on their own Windows devices. If admins choose not to allow it, they can manually deploy apps to users instead.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isMicrosoft365AppsEnabled | Boolean | Specifies whether users can install Microsoft 365 apps, including Skype for Business, on their Windows devices. The default value is `true`. |
| isProjectEnabled | Boolean | Specifies whether users can install Microsoft Project on their Windows devices. The default value is `true`. |
| isSkypeForBusinessEnabled | Boolean | Specifies whether users can install Skype for Business \(standalone\) on their Windows devices. The default value is `true`. |
| isVisioEnabled | Boolean | Specifies whether users can install Visio on their Windows devices. The default value is `true`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appsInstallationOptionsForWindows",
  "isMicrosoft365AppsEnabled": "Boolean",
  "isProjectEnabled": "Boolean",
  "isSkypeForBusinessEnabled": "Boolean",
  "isVisioEnabled": "Boolean"
}
```
