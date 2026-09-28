<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplatecategory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-26 -->

# applicationTemplateCategory resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a single category that can appear in the `categories` property of an [applicationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-beta). Each category exposes both the underlying value used by the API and a localizable display name suitable for showing in a UI.

Use the [applicationTemplate: categories](https://learn.microsoft.com/en-us/graph/api/applicationtemplate-categories?view=graph-rest-beta) function to retrieve the full list of supported categories.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The localizable display name of the category, suitable for showing in a UI. |
| value | String | The category value as it appears in the `categories` property of an [applicationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-beta). Use this value when filtering application templates by category. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.applicationTemplateCategory",
  "displayName": "String",
  "value": "String"
}
```
