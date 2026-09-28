<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/search/resources/copilotsearchhit -->
<!-- Sitemap-Last-Modified: 2025-10-20 -->

# copilotSearchHit resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a single search result from a search query.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `webUrl` | String | Direct URL to access the search result. |
| `preview` | String | Short, verbatim text snippet from the file, providing a preview of the search result |
| `resourceType` | String | Type of the resource \(for example, `driveItem`, `listItem`\). |
| `resourceMetadata` | [copilotSearchResourceMetadataDictionary](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/search/resources/copilotsearchresourcemetadatadictionary) | Requested metadata fields \(only included if specified in request\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotSearchHit",
  "webUrl": "String",
  "preview": "String",
  "resourceType": "String",
  "resourceMetadata": {
    "@odata.type": "microsoft.graph.copilotSearchResourceMetadataDictionary"
  }
}
```
