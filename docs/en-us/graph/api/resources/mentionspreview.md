<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mentionspreview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# mentionsPreview resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information about [mention](https://learn.microsoft.com/en-us/graph/api/resources/mention?view=graph-rest-beta) objects in a resource instance.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isMentioned | Boolean | True if the signed-in user is mentioned in the parent resource instance. Read-only. Supports filter. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isMentioned": "Boolean"
}
```
