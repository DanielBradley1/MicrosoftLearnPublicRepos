<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-21 -->

# sharePointRoot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the root container for SharePoint resources and services in Microsoft Graph. This resource provides access to SharePoint migration operations and other SharePoint-related functionality.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **sharePointRoot** resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| migrations | [sharePointMigrationsRoot](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationsroot?view=graph-rest-beta) | The migration operations for cross-organization SharePoint migrations. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointRoot",
  "id": "String (identifier)"
}
```
