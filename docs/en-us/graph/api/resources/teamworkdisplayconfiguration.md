<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkdisplayconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkDisplayConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the display configuration for a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuredDisplays | [teamworkConfiguredPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkconfiguredperipheral?view=graph-rest-beta) collection | The list of configured displays. Applicable only for Microsoft Teams Rooms devices. |
| displayCount | Int32 | Total number of connected displays, including the inbuilt display. Applicable only for Teams Rooms devices. |
| inBuiltDisplayScreenConfiguration | [teamworkDisplayScreenConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdisplayscreenconfiguration?view=graph-rest-beta) | Configuration for the inbuilt display. Not applicable for Teams Rooms devices. |
| isContentDuplicationAllowed | Boolean | `True` if content duplication is allowed. Applicable only for Teams Rooms devices. |
| isDualDisplayModeEnabled | Boolean | `True` if dual display mode is enabled. If **isDualDisplayModeEnabled** is `true`, then the content will be displayed on both front of room screens instead of just the one screen, when it is shared via the HDMI ingest module on the Microsoft Teams Rooms device. Applicable only for Teams Rooms devices. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkDisplayConfiguration",
  "configuredDisplays": [
    {
      "@odata.type": "microsoft.graph.teamworkConfiguredPeripheral"
    }
  ],
  "displayCount": "Integer",
  "inBuiltDisplayScreenConfiguration": {
    "@odata.type": "microsoft.graph.teamworkDisplayScreenConfiguration"
  },
  "isContentDuplicationAllowed": "Boolean",
  "isDualDisplayModeEnabled": "Boolean"
}
```
