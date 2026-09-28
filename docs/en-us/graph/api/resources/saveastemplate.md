<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/saveastemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-17 -->

# saveAsTemplate resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the required fields to save page as a template in SharePoint.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| title | String | The title of the site page template to create. Optional. |
| name | String | The name of the site page template to create. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "title": "String",
  "name": "String"
}
```
