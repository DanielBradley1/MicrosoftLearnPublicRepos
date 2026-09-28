<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/documentset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# documentSet resource type

Namespace: microsoft.graph

Represents a document set in SharePoint. A document set is a group of related documents that you can manage as a single entity.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedContentTypes | Collection\(microsoft.graph.contentTypeInfo\) | Content types allowed in document set. |
| defaultContents | Collection\(microsoft.graph.documentSetContent\) | Default contents of document set. |
| propagateWelcomePageChanges | Boolean | Specifies whether to push welcome page changes to inherited content types. |
| shouldPrefixNameToFile | Boolean | Indicates whether to add the name of the document set to each file name. |
| welcomePageUrl | string | Welcome page absolute URL. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sharedColumns | Collection\(microsoft.graph.columnDefinition\) | Columns edited on the document set that synchronize to all documents in the set. These are read-only on the documents themselves. |
| welcomePageColumns | Collection\(microsoft.graph.columnDefinition\) | Specifies columns to show on the welcome page for the document set. |

## JSON representation

The following is a JSON representation of a **documentSet** resource.

```json
{
  "allowedContentTypes": [{ "@type": "microsoft.graph.contentTypeInfo" }],
  "defaultContents": [{ "@type": "microsoft.graph.documentSetContent" }],
  "propagateWelcomePageChanges": false,
  "shouldPrefixNameToFile": true,
  "welcomePageUrl": "string"
}
```
