<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printpagerange?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# printPageRange resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies the range of pages to be printed.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| startPage | Int32 | The start page \(inclusive\) for the range. Read-only. |
| endPage | Int32 | The end page \(inclusive\) for the range. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "startPage": "Int32",
  "endPage": "Int32"
}
```
