<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/resources/copilotconversationresponsemessage -->
<!-- Sitemap-Last-Modified: 2025-10-17 -->

# copilotConversationResponseMessage resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a message in a Copilot conversation being continued through the [Microsoft 365 Copilot Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/copilotroot-post-conversations).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `adaptiveCards` | Edm.Untyped collection | List of raw JSON representations of adaptive cards. This property may be empty. |
| `attributions` | [copilotConversationAttribution](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/resources/copilotconversationattribution) collection | The list of attributions \(either citations or annotations\) included in the chat message response. |
| `createdDateTime` | DateTimeOffset | The timestamp when the chat message was created. |
| `id` | String | The identifier for the Copilot conversation. This is used as a path parameter when continuing a synchronous or streamed conversation. |
| `sensitivityLabel` | [searchSensitivityLabelInfo](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/resources/searchsensitivitylabelinfo) | Defines the highest sensitivity \(most restricted\) resource used to create the chat message. |
| `text` | String | The chat message text. This either recaps the submitted prompt or articulates the Microsoft 365 Copilot Chat API's response. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotConversationResponseMessage",
  "id": "String",
  "text": "String",
  "createdDateTime": "DateTimeOffset",
  "adaptiveCards": [
    {
      "@odata.type": "#microsoft.graph.Edm.Untyped"
    }
  ],
  "attributions": [
    {
      "@odata.type": "#microsoft.graph.copilotConversationAttribution"
    }
  ],
  "sensitivityLabel": {
    "@odata.type": "#microsoft.graph.searchSensitivityLabelInfo"
  }
}
```
