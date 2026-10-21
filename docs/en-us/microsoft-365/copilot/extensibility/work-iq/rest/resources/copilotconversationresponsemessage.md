<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversationresponsemessage -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Work IQ - copilotConversationResponseMessage resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

Represents a message in a Copilot conversation being continued through the [Work IQ Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotroot-post-conversations).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `adaptiveCards` | Edm.Untyped collection | List of raw JSON representations of adaptive cards. This property may be empty. |
| `attributions` | [copilotConversationAttribution](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversationattribution) collection | The citations and annotations included in the message. This property is an empty collection when the message has no attributions. |
| `createdDateTime` | DateTimeOffset | The timestamp when the chat message was created. |
| `id` | String | The unique identifier of the message. |
| `references` | [copilotConversationReferenceMap](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversationreferencemap) | A keyed map of conversation references. |
| `sensitivityLabel` | [searchSensitivityLabelInfo](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/searchsensitivitylabelinfo) | Defines the highest sensitivity \(most restricted\) resource used to create the chat message. |
| `text` | String | The chat message text. This either recaps the submitted prompt or articulates the Work IQ Chat API's response. |

Use `attributions` to render the citations and annotations associated with response text. Each attribution identifies its type, source, display text, destination URL, and optional image metadata. The `references` property is a separate keyed map of conversation reference metadata.

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
  "references": {
    "@odata.type": "#microsoft.graph.copilotConversationReferenceMap"
  },
  "sensitivityLabel": {
    "@odata.type": "#microsoft.graph.searchSensitivityLabelInfo"
  }
}
```
