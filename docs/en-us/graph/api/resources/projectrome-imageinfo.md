<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/projectrome-imageinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# imageInfo resource type

Namespace: microsoft.graph

A complex type for representing the **attribution** property in the [visualInfo](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-visualinfo?view=graph-rest-1.0) part of the [activity](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-activity?view=graph-rest-1.0) object.

## Properties

| Name | Type | Description |
| :--- | :--- | :--- |
| addImageQuery | Boolean | Optional; parameter used to indicate the server is able to render image dynamically in response to parameterization. For example – a high contrast image |
| alternateText | String | Optional; alt-text accessible content for the image |
| iconUrl | String | Optional; URI that points to an icon which represents the application used to generate the activity |

## JSON Representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "microsoft.graph.imageInfo",
    "iconUrl": "String (URL)",
    "alternateText": "String",
    "addImageQuery": "boolean"
}
```
