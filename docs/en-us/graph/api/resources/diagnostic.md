<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/diagnostic?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# diagnostic resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Information about an error or warning for a OneNote operation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| message | String | The message describing the condition that triggered the error or warning. |
| url | String | The link to the documentation for this issue. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "message": "string",
  "url": "string"
}
```
