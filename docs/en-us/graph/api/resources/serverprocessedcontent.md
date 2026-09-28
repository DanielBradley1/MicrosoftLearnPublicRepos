<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serverprocessedcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# serverProcessedContent resource type

Namespace: microsoft.graph

Represents the server processed content of a given web part.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| componentDependencies | [metaDataKeyStringPair](https://learn.microsoft.com/en-us/graph/api/resources/metadatakeystringpair?view=graph-rest-1.0) collection | A key-value map where keys are string identifiers and values are component ids. SharePoint servers might decide to use this hint to preload the script for corresponding components for performance boost. |
| customMetadata | [metaDataKeyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/metadatakeyvaluepair?view=graph-rest-1.0) collection | A key-value map where keys are string identifier and values are object of custom key-value pair. |
| htmlStrings | [metaDataKeyStringPair](https://learn.microsoft.com/en-us/graph/api/resources/metadatakeystringpair?view=graph-rest-1.0) collection | A key-value map where keys are string identifiers and values are rich text with HTML format. SharePoint servers treat the values as HTML content and run services like safety checks, search index and link fixup on them. |
| imageSources | [metaDataKeyStringPair](https://learn.microsoft.com/en-us/graph/api/resources/metadatakeystringpair?view=graph-rest-1.0) collection | A key-value map where keys are string identifiers and values are image sources. SharePoint servers treat the values as image sources and run services like search index and link fixup on them. |
| links | [metaDataKeyStringPair](https://learn.microsoft.com/en-us/graph/api/resources/metadatakeystringpair?view=graph-rest-1.0) collection | A key-value map where keys are string identifiers and values are links. SharePoint servers treat the values as links and run services like link fixup on them. |
| searchablePlainTexts | [metaDataKeyStringPair](https://learn.microsoft.com/en-us/graph/api/resources/metadatakeystringpair?view=graph-rest-1.0) collection | A key-value map where keys are string identifiers and values are strings that should be search indexed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serverProcessedContent",
  "htmlStrings": [
    {
      "@odata.type": "microsoft.graph.metaDataKeyStringPair"
    }
  ],
  "searchablePlainTexts": [
    {
      "@odata.type": "microsoft.graph.metaDataKeyStringPair"
    }
  ],
  "links": [
    {
      "@odata.type": "microsoft.graph.metaDataKeyStringPair"
    }
  ],
  "imageSources": [
    {
      "@odata.type": "microsoft.graph.metaDataKeyStringPair"
    }
  ],
  "componentDependencies": [
    {
      "@odata.type": "microsoft.graph.metaDataKeyStringPair"
    }
  ],
  "customMetadata": [
    {
      "@odata.type": "microsoft.graph.metaDataKeyValuePair"
    }
  ]
}
```
