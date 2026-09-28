<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/numbercolumn?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# NumberColumn resource type

Namespace: microsoft.graph

The **numberColumn** on a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) resource indicates that the column's values are numbers.

## JSON representation

Here is a JSON representation of a **numberColumn** resource.

```json
{
  "decimalPlaces": "automatic | none | one | two | three | four | five",
  "displayAs": "number | percentage",
  "maximum": 10.551,
  "minimum": 99.993
}
```

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| **decimalPlaces** | string | How many decimal places to display. See below for information about the possible values. |
| **displayAs** | string | How the value should be presented in the UX. Must be one of `number` or `percentage`. If unspecified, treated as `number`. |
| **maximum** | double | The maximum permitted value. |
| **minimum** | double | The minimum permitted value. |

## DecimalPlaces

| Value | Description |
| :--- | :--- |
| **automatic** | Default. Automatically display decimal places as needed. |
| **none** | Do not display any decimal places. |
| **one** | Always display one decimal place. |
| **two** | Always display two decimal places. |
| **three** | Always display three decimal places. |
| **four** | Always display four decimal places. |
| **five** | Always display five decimal places. |

Note: **decimalPlaces** and **displayAs** apply to how numbers are rendered, not stored. These properties may be updated.
