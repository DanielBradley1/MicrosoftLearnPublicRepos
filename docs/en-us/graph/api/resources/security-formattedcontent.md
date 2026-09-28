<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-formattedcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# formattedContent resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

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
