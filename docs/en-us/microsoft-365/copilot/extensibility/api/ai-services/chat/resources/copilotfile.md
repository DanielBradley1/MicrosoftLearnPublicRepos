<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/resources/copilotfile -->
<!-- Sitemap-Last-Modified: 2025-10-17 -->

# copilotFile resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

OneDrive or SharePoint file being sent as context into a Copilot conversation through the [Microsoft 365 Copilot Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/copilotroot-post-conversations).

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
