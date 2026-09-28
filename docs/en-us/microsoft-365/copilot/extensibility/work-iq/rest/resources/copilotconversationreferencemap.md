<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversationreferencemap -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Work IQ - copilotConversationReferenceMap resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

A keyed map of [copilotConversationReference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversationreference) objects.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotConversationReferenceMap",
  "key-1": {
    "@odata.type": "#microsoft.graph.copilotConversationReference"
  },
  "key-2": {
    "@odata.type": "#microsoft.graph.copilotConversationReference"
  }
}
```
