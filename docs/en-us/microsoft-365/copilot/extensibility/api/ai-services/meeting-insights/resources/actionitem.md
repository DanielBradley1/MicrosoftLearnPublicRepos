<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/actionitem -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# actionItem resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents an action item associated with a [call AI insight](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/callaiinsight).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `ownerDisplayName` | String | The display name of the owner of the action item. |
| `text` | String | The text content of the action item. |
| `title` | String | The title of the action item. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.actionItem",
  "ownerDisplayName": "String",
  "text": "String",
  "title": "String"
}
```
