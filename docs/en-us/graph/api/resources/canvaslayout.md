<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/canvaslayout?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# canvasLayout resource type

Namespace: microsoft.graph

Represents the layout of the content in a given SharePoint page.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| horizontalSections | [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) collection | Collection of horizontal sections on the SharePoint page. |
| verticalSection | [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) | Vertical section on the SharePoint page. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.canvasLayout",
  "id": "String (identifier)",
  /* relationships */
  "horizontalSections": {
    "@odata.type": "Collection(microsoft.graph.horizontalSection)"
  },
  "verticalSection": { "@odata.type": "microsoft.graph.verticalSection" }
}
```
