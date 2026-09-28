<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resulttemplateoption?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# resultTemplateOption resource type

Namespace: microsoft.graph

Provides the search result template options to render search results from connectors.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enableResultTemplate | Boolean | Indicates whether search display layouts are enabled. If enabled, the user will get the result template to render the search results content in the **resultTemplates** property of the [response](https://learn.microsoft.com/en-us/graph/api/resources/searchresponse). The result template is based on [Adaptive Cards](https://adaptivecards.io/). Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
 {
    "enableResultTemplate": "Boolean"
 }
```
