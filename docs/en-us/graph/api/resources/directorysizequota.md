<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/directorysizequota?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# directorySizeQuota resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the used and total directory quota for an [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| total | Int32 | Total amount of the directory quota. |
| used | Int32 | Used amount of the directory quota. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "total": "Int32",
  "used": "Int32"
}
```
