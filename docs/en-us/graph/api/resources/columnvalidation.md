<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/columnvalidation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# columnValidation resource type

Namespace: microsoft.graph

Represents properties that validates column values.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| **defaultLanguage** | string | Default BCP 47 language tag for the description. |
| **descriptions** | Collection\(microsoft.graph.displayNameLocalization\) | Localized messages that explain what is needed for this column's value to be considered valid. User will be prompted with this message if validation fails. |
| **formula** | string | The formula to validate column value. For examples, see [Examples of common formulas in lists](https://support.microsoft.com/office/examples-of-common-formulas-in-sharepoint-lists-d81f5f21-2b4e-45ce-b170-bf7ebf6988b3). |

SharePoint formulas use a syntax similar to Excel formulas. For more information, see [Examples of common formulas in SharePoint Lists](https://support.office.com/article/Examples-of-common-formulas-in-SharePoint-Lists-d81f5f21-2b4e-45ce-b170-bf7ebf6988b3).

## JSON representation

The following is a JSON representation of a **columnValidation** resource.

```json
{
  "defaultLanguage": "string",
  "descriptions": [{ "@type": "microsoft.graph.displayNameLocalization" }],
  "formula": "string"
}
```
