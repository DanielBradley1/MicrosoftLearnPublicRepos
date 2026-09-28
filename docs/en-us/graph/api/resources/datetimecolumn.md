<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/datetimecolumn?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# DateTimeColumn resource type

Namespace: microsoft.graph

The **dateTimeColumn** on a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) resource indicates that the column's values are dates or times.

## JSON representation

Here's a JSON representation of a **dateTimeColumn** resource.

```json
{
  "displayAs": "default | friendly | standard",
  "format": "dateOnly | dateTime"
}
```

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| **displayAs** | string | How the value should be presented in the UX. Must be one of `default`, `friendly`, or `standard`. See below for more details. If unspecified, treated as `default`. |
| **format** | string | Indicates whether the value should be presented as a date only or a date and time. Must be one of `dateOnly` or `dateTime` |

## DisplayAs options

| Value | Description |
| :--- | :--- |
| **default** | Uses the default rendering in the UX. |
| **friendly** | Uses a friendly relative representation \(for example "today at 3:00 PM"\) |
| **standard** | Uses the standard absolute representation \(for example "5/10/2017 3:20 PM"\) |
