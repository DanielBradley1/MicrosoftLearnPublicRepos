<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/textwebpart?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# textWebPart resource type

Namespace: microsoft.graph

Represents a text web part instance on a SharePoint page.

Inherits from [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Instance identifier of the web part. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| innerHtml | String | The HTML string in text web part. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.textWebPart",
  "id": "String (identifier)",
  "innerHtml": "String"
}
```
