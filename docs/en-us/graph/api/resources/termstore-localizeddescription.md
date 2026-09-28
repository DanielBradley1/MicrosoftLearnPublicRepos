<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/termstore-localizeddescription?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# localizedDescription resource type

Namespace: microsoft.graph.termStore

Represents the localized description used to describe a [term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) in the term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description in the localized language. |
| languageTag | String | The language tag for the label. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.termStore.localizedDescription",
  "description": "String",
  "languageTag": "String"
}
```
