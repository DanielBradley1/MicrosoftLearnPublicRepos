<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversationrequestmessageparameter -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Work IQ - copilotConversationRequestMessageParameter resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

Represents a chat message being sent into a Copilot conversation through the [Work IQ Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotroot-post-conversations).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `text` | String | The text of the chat message. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotConversationRequestMessageParameter",
  "text": "String"
}
```
