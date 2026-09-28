<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudclipboarditempayload?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-21 -->

# cloudClipboardItemPayload resource type

Namespace: microsoft.graph

Contains the specific details of the content found within a [cloudClipboardItem](https://learn.microsoft.com/en-us/graph/api/resources/cloudclipboarditem?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | The `formatName` version of the value of a cloud clipboard **encoded in base64**. |
| formatName | String | For a list of possible values see [formatName values](#formatname-values). |

### formatName values

| Name | Description | Windows clipboard format |
| :--- | :--- | :--- |
| AnsiTextBase64 | ANSI text format | CF\_TEXT |
| TextBase64 | Unicode text format | CF\_UNICODETEXT |
| UniformResourceLocatorWBase64 | Unicode URI format | [CFSTR\_INETURLW](https://learn.microsoft.com/en-us/windows/win32/shell/clipboard#cfstr_ineturl) |
| UniformResourceLocatorBase64 | ANSI URI format | [CFSTR\_INETURLA](https://learn.microsoft.com/en-us/windows/win32/shell/clipboard#cfstr_ineturl) |
| RichTextFormatBase64 | Rich text format | [Registered Clipboard Format](https://learn.microsoft.com/en-us/windows/win32/dataxchg/clipboard-formats#registered-clipboard-formats) |
| HTMLFormatBase64 | HTML format | [CF\_HTML](https://learn.microsoft.com/en-us/windows/win32/dataxchg/html-clipboard-format) |
| {Custom} | Custom format defined by clients to identify application-specific formats. The client that creates it can only understand it and handle it. | NA |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudClipboardItemPayload",
  "content": "String",
  "formatName": "String"
}
```
