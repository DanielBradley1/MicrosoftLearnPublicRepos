<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerappliedcategories?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# plannerAppliedCategories resource type

Namespace: microsoft.graph

The **AppliedCategoriesCollection** resource represents the collection of categories \(or labels\) that have been applied to a task. It's part of the [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) object. There can be up to six categories applied to a task. Category descriptions, for example, `category1`, `category2` etc., are part of the [plan details](https://learn.microsoft.com/en-us/graph/api/resources/plannerplandetails?view=graph-rest-1.0) object. This is an open type.

## Properties

Properties of an Open Type can be defined by the client. In this case though, the client must provide `category1`, `category2`, `category3`, `category4`, `category5` and/or `category6` as properties with their values being the `true` Boolean when the corresponding categories are applied on the task. When they don't apply, properties are automatically removed by setting their values to the `false` Boolean.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "String-value": true
}
```

Example:

```json
{
  "category1": true,
  "category3": true,
  "category5": true
}
```
