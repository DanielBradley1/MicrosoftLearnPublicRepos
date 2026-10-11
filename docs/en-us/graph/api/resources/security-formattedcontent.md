<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-formattedcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-21 -->

# formattedContent resource type

Namespace: microsoft.graph.security

Note

The Microsoft Threat Intelligence APIs are available to all customers with a Microsoft Defender XDR or Microsoft Sentinel license. No separate license is required to access these APIs.

Represents formatted data content, and indicates both the content and format of that data. This resource doesn't represent large binary contents.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | The content of this **formattedContent**. |
| format | microsoft.graph.security.contentFormat | The format of the content. The possible values are: `text`, `html`, `markdown`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.formattedContent",
  "content": "String",
  "format": "String"
}
```
