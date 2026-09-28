<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosminimumoperatingsystem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# macOSMinimumOperatingSystem resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The minimum operating system required for a macOS app.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| v10\_7 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 10.7 or later is required to install the app. If 'False', OS X Version 10.7 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v10\_8 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 10.8 or later is required to install the app. If 'False', OS X Version 10.8 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v10\_9 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 10.9 or later is required to install the app. If 'False', OS X Version 10.9 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v10\_10 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 10.10 or later is required to install the app. If 'False', OS X Version 10.10 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v10\_11 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 10.11 or later is required to install the app. If 'False', OS X Version 10.11 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v10\_12 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 10.12 or later is required to install the app. If 'False', OS X Version 10.12 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v10\_13 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 10.13 or later is required to install the app. If 'False', OS X Version 10.13 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v10\_14 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 10.14 or later is required to install the app. If 'False', OS X Version 10.14 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v10\_15 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 10.15 or later is required to install the app. If 'False', OS X Version 10.15 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v11\_0 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 11.0 or later is required to install the app. If 'False', OS X Version 11.0 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v12\_0 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 12.0 or later is required to install the app. If 'False', OS X Version 12.0 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |
| v13\_0 | Boolean | Indicates the minimum OS X version support required for the managed device. When 'True', macOS with OS X 13.0 or later is required to install the app. If 'False', OS X Version 13.0 is not the minimum version. Default value is False. Exactly one of the minimum operating system boolean values will be TRUE. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSMinimumOperatingSystem",
  "v10_7": true,
  "v10_8": true,
  "v10_9": true,
  "v10_10": true,
  "v10_11": true,
  "v10_12": true,
  "v10_13": true,
  "v10_14": true,
  "v10_15": true,
  "v11_0": true,
  "v12_0": true,
  "v13_0": true
}
```
