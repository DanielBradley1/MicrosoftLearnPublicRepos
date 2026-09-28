<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sizerange?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# sizeRange resource type

Namespace: microsoft.graph

Specifies the maximum and minimum sizes \(in kilobytes\) that an incoming message must have in order for a condition or exception to apply.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| maximumSize | Int32 | The maximum size \(in kilobytes\) that an incoming message must have in order for a condition or exception to apply. |
| minimumSize | Int32 | The minimum size \(in kilobytes\) that an incoming message must have in order for a condition or exception to apply. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "maximumSize": "Int32",
  "minimumSize": "Int32"
}
```
