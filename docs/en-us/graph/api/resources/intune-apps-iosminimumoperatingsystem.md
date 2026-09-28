<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosminimumoperatingsystem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# iosMinimumOperatingSystem resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties of the minimum operating system required for an iOS mobile app.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| v8\_0 | Boolean | Indicates the minimum iOS version support required for the managed device. When 'True', iOS with OS Version 8.0 or later is required to install the app. If 'False', iOS Version 8.0 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v9\_0 | Boolean | Indicates the minimum iOS version support required for the managed device. When 'True', iOS with OS Version 9.0 or later is required to install the app. If 'False', iOS Version 9.0 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v10\_0 | Boolean | Indicates the minimum iOS version support required for the managed device. When 'True', iOS with OS Version 10.0 or later is required to install the app. If 'False', iOS Version 10.0 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v11\_0 | Boolean | Indicates the minimum iOS version support required for the managed device. When 'True', iOS with OS Version 11.0 or later is required to install the app. If 'False', iOS Version 11.0 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v12\_0 | Boolean | Indicates the minimum iOS version support required for the managed device. When 'True', iOS with OS Version 12.0 or later is required to install the app. If 'False', iOS Version 12.0 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v13\_0 | Boolean | Indicates the minimum iOS version support required for the managed device. When 'True', iOS with OS Version 13.0 or later is required to install the app. If 'False', iOS Version 13.0 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v14\_0 | Boolean | Indicates the minimum iOS version support required for the managed device. When 'True', iOS with OS Version 14.0 or later is required to install the app. If 'False', iOS Version 14.0 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v15\_0 | Boolean | Indicates the minimum iOS version support required for the managed device. When 'True', iOS with OS Version 15.0 or later is required to install the app. If 'False', iOS Version 15.0 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosMinimumOperatingSystem",
  "v8_0": true,
  "v9_0": true,
  "v10_0": true,
  "v11_0": true,
  "v12_0": true,
  "v13_0": true,
  "v14_0": true,
  "v15_0": true
}
```
