<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/filterdatetime?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-13 -->

# workbookFilterDatetime resource type

Namespace: microsoft.graph

Represents how to filter a date when filtering on values.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| date | String | The date in ISO 8601 format used to filter data. |
| specificity | String | Defines how specific you should use the **date** to keep data. For example, if the date is `2005-04-02` and the **specificity** property is set to `month`, the filter operation keeps all rows with a date in the month of April 2009. The possible values are: `Year`, `Month`, `Day`, `Hour`, `Minute`, `Second`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "date": "String",
  "specificity": "String"
}
```
