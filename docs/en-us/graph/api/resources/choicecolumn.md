<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/choicecolumn?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# ChoiceColumn resource type

Namespace: microsoft.graph

The **choiceColumn** on a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) resource indicates that the column's values can be selected from a list of choices.

## JSON representation

Here is a JSON representation of a **choiceColumn** resource.

```json
{
  "allowTextEntry": true,
  "choices": ["red", "blue", "green"],
  "displayAs": "checkBoxes | dropDownMenu | radioButtons"
}
```

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| **allowTextEntry** | Boolean | If true, allows custom values that aren't in the configured choices. |
| **choices** | collection\(string\) | The list of values available for this column. |
| **displayAs** | string | How the choices are to be presented in the UX. Must be one of `checkBoxes`, `dropDownMenu`, or `radioButtons` |
