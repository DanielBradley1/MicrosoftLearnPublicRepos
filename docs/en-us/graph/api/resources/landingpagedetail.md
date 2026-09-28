<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/landingpagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# landingPageDetail resource type

Namespace: microsoft.graph

Represents an attack simulation landing page detail.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | Landing page detail content. |
| id | String | Unique identifier for the **landingPageDetail** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isDefaultLangauge | Boolean | Indicates whether this language detail is default for the landing page. |
| language | String | The content language for the landing page. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.landingPageDetail",
  "content": "String",
  "id": "String (identifier)",
  "isDefaultLangauge": "Boolean",
  "language": "String"
}
```
