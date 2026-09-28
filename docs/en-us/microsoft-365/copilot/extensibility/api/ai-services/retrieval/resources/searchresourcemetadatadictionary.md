<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/searchresourcemetadatadictionary -->
<!-- Sitemap-Last-Modified: 2025-10-24 -->

# searchResourceMetadataDictionary resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a metadata dictionary in a [retrievalHit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/retrievalhit). This resource is an open type. For more information on open types, see [Open Type](https://www.odata.org/getting-started/advanced-tutorial/#openType).

The property names in the dictionary correspond to the list of metadata fields requested in the `resourceMetadata` parameter to the [retrieval API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/copilotroot-retrieval). The property values are string representations of the value of the corresponding metadata fields.

## JSON representation

The following JSON representation shows the resource type. For example, if the requested metadata fields are `title` and `author`, the resulting dictionary is:

```json
{
  "@odata.type": "#microsoft.graph.searchResourceMetadataDictionary",
  "title": "String",
  "author": "String"
}
```
