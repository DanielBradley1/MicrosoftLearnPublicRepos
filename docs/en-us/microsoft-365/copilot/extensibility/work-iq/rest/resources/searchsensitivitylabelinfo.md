<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/searchsensitivitylabelinfo -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Work IQ - searchSensitivityLabelInfo resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

Describes the information protection label that details how to properly apply a sensitivity label to information.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `color` | String | The color that the UI should display for the label, if configured. |
| `displayName` | String | The display name for the sensitivity label |
| `priority` | Int32 | The priority in which the sensitivity label is applied. |
| `sensitivityLabelId` | String | The ID of the sensitivity label. |
| `tooltip` | String | The tooltip that should be displayed for the label in a UI. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.searchSensitivityLabelInfo",
  "sensitivityLabelId": "String",
  "displayName": "String",
  "tooltip": "String",
  "priority": "Integer",
  "color": "String"
}
```
