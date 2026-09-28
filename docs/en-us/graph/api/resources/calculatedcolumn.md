<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/calculatedcolumn?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# calculatedColumn resource type

Namespace: microsoft.graph

The **calculatedColumn** on a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) resource indicates that the data of the column is calculated based on other columns in the site.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| format | String | For `dateTime` output types, the format of the value. The possible values are: `dateOnly` or `dateTime`. |
| formula | String | The formula used to compute the value for this column. |
| outputType | String | The output type used to format values in this column. The possible values are: `boolean`, `currency`, `dateTime`, `number`, or `text`. |

SharePoint formulas use a syntax similar to Excel formulas. For more information, see [Examples of common formulas in SharePoint Lists](https://support.office.com/en-us/article/Examples-of-common-formulas-in-SharePoint-Lists-d81f5f21-2b4e-45ce-b170-bf7ebf6988b3).

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "format": "String",
  "formula": "String",
  "outputType": "String"
}
```
