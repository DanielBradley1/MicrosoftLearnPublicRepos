<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/directoryrolemanagementdeleteditemcontainer?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# directoryRoleManagementDeletedItemContainer resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains soft-deleted custom [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) objects for Microsoft Entra directory role management. Use this container to list, inspect, restore, or permanently delete custom role definitions that have been soft-deleted.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List role definitions](https://learn.microsoft.com/en-us/graph/api/directoryrolemanagementdeleteditemcontainer-list-roledefinitions?view=graph-rest-beta) | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) collection | List soft-deleted custom role definitions. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the container. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| roleDefinitions | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) collection | The soft-deleted custom role definitions in the directory. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.directoryRoleManagementDeletedItemContainer",
  "id": "String (identifier)"
}
```
