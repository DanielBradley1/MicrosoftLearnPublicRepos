<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contentmanagementroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# contentManagementRoot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides the entry point under `/security` for connected source-control repositories.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List repositories](https://learn.microsoft.com/en-us/graph/api/contentmanagementroot-list-repositories?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) collection | Get the source-control repositories connected to the tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | A unique identifier for this resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| repositories | [microsoft.graph.security.contentManagement.contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) collection | Connected source-control repositories that deliver security content as code. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.contentManagementRoot",
  "id": "String (identifier)"
}
```
