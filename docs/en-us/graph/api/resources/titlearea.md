<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/titlearea?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# titleArea resource type

Namespace: microsoft.graph

Represents the title area of a given SharePoint page.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alternativeText | String | Alternative text on the title area. |
| enableGradientEffect | Boolean | Indicates whether the title area has a gradient effect enabled. |
| imageWebUrl | String | URL of the image in the title area. |
| layout | [titleAreaLayoutType](https://learn.microsoft.com/en-us/graph/api/resources/titlearea?view=graph-rest-1.0#titlearealayouttype-values) | Enumeration value that indicates the layout of the title area. The possible values are: `imageAndTitle`, `plain`, `colorBlock`, `overlap`, `unknownFutureValue`. |
| serverProcessedContent | [serverProcessedContent](https://learn.microsoft.com/en-us/graph/api/resources/serverprocessedcontent?view=graph-rest-1.0) | Contains collections of data that can be processed by server side services like search index and link fixup. |
| showAuthor | Boolean | Indicates whether the author should be shown in title area. |
| showPublishedDate | Boolean | Indicates whether the published date should be shown in title area. |
| showTextBlockAboveTitle | Boolean | Indicates whether the text block above title should be shown in title area. |
| textAboveTitle | String | The text above title line. |
| textAlignment | [titleAreaTextAlignmentType](https://learn.microsoft.com/en-us/graph/api/resources/titlearea?view=graph-rest-1.0#titleareatextalignmenttype-values) | Enumeration value that indicates the text alignment of the title area. The possible values are: `left`, `center`, `unknownFutureValue`. |

### titleAreaLayoutType values

| Member | Description |
| :--- | :--- |
| imageAndTitle | The title area has an image and title layout. |
| plain | The title area has a plain layout. |
| colorBlock | The title area has a color block layout. |
| overlap | The title area has an overlap layout. |
| unknownFutureValue | Marker value for future compatibility. |

### titleAreaTextAlignmentType values

| Member | Description |
| :--- | :--- |
| left | The text in title area is left-aligned. |
| center | The text in title area is center-aligned. |
| unknownFutureValue | Marker value for future compatibility. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.titleArea",
  "alternativeText": "String",
  "enableGradientEffect": "Boolean",
  "imageWebUrl": "String",
  "layout": "String",
  "serverProcessedContent": {
    "@odata.type": "microsoft.graph.serverProcessedContent"
  },
  "showAuthor": "Boolean",
  "showPublishedDate": "Boolean",
  "showTextBlockAboveTitle": "Boolean",
  "textAboveTitle": "String",
  "textAlignment": "String"
}
```
