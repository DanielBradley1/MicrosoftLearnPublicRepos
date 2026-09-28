<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotfile -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Work IQ - copilotFile resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

OneDrive or SharePoint file being sent as context into a Copilot conversation through the [Work IQ Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotroot-post-conversations).

Use a `copilotFile` in the [copilotContextualResources](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotcontextualresources) `files` collection to ground a chat message with a OneDrive or SharePoint file. The [copilotConversationRequestMessageParameter](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversationrequestmessageparameter) contains the prompt text, while [copilotContextMessage](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotcontextmessage) provides additional text context.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `uri` | String | The URI of the OneDrive or SharePoint file. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotFile",
  "uri": "String"
}
```
