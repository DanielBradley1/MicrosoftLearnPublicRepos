<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/visualproperties?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# visualProperties resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the visual content, namely title and body, of a visual notification targeted to a user.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| title | String | The title of a visual user notification. This field is required for visual notification payloads. |
| body | String | The body of a visual user notification. Body is optional. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "title": "String",
  "body": "String"
}
```
