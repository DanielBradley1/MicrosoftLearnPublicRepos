<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-workbookcontent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# workbookContent resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the JSON document stored in the **content** property of a [workbook](https://learn.microsoft.com/en-us/graph/api/resources/security-workbook?view=graph-rest-beta).

Inherits from [microsoft.graph.Dictionary](https://learn.microsoft.com/en-us/graph/api/resources/dictionary?view=graph-rest-beta).

This resource is an open type. It accepts dynamic properties whose values are represented by `microsoft.graph.Json`. Those values can be JSON objects, arrays, strings, numbers, Boolean values, or `null`.

The **content** property must be a JSON object, not a JSON-encoded string or a top-level array. When you update a workbook, supply the complete object. The update replaces the existing document rather than merging its nested properties.

## Properties

None. Properties are defined dynamically in the JSON document.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.workbookContent"
}
```
