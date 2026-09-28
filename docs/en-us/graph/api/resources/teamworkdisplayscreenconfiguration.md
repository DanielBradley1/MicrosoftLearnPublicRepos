<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkdisplayscreenconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkDisplayScreenConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represent the details about the display screen configuration for a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| backlightBrightness | Int32 | The brightness level on the device \(0-100\). Not applicable for Microsoft Teams Rooms devices. |
| backlightTimeout | Duration | Timeout for backlight \(30-3600 secs\). Not applicable for Teams Rooms devices. |
| isHighContrastEnabled | Boolean | `True` if high contrast mode is enabled. Not applicable for Teams Rooms devices. |
| isScreensaverEnabled | Boolean | `True` if screensaver is enabled. Not applicable for Teams Rooms devices. |
| screensaverTimeout | Duration | Screensaver timeout from 30 to 3600 secs. Not applicable for Teams Rooms devices. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkDisplayScreenConfiguration",
  "backlightBrightness": "Integer",
  "backlightTimeout": "String (duration)",
  "isHighContrastEnabled": "Boolean",
  "isScreensaverEnabled": "Boolean",
  "screensaverTimeout": "String (duration)"
}
```
