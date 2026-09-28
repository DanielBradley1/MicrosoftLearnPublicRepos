<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/termstore-localizedname?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# localizedName resource type

Namespace: microsoft.graph.termStore

Represents the localized name used in the term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0), which identifies the name in the localized language. For more information, see [localizedLabel](https://learn.microsoft.com/en-us/graph/api/resources/termstore-localizedlabel?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| languageTag | String | The language tag for the label. |
| name | String | The name in the localized language. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.termStore.localizedName",
  "name": "String",
  "languageTag": "String"
}
```
