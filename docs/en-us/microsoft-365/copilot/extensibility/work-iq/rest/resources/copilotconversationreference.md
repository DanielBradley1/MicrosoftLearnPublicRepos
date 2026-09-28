<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversationreference -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Work IQ - copilotConversationReference resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

Represents a conversation reference.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `isCitedInResponse` | Boolean | **TODO: Add description** |
| `sensitivityLabel` | [searchSensitivityLabelInfo](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/searchsensitivitylabelinfo) | **TODO: Add description** |
| `targetLink` | String | **TODO: Add description** |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotConversationReference",
  "targetLink": "String",
  "sensitivityLabel": {
    "@odata.type": "microsoft.graph.searchSensitivityLabelInfo"
  },
  "isCitedInResponse": true
}
```
