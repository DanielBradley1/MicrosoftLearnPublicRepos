<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/termstore-localizedlabel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# localizedLabel resource type

Namespace: microsoft.graph.termStore

Represents the label for a [term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) in the term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0).

Identifies the labels associated with a given term.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isDefault | Boolean | Indicates whether the label is the default label. |
| languageTag | String | The language tag for the label. |
| name | String | The name of the label. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.termStore.localizedLabel",
  "name": "String",
  "isDefault": "Boolean",
  "languageTag": "String"
}
```
