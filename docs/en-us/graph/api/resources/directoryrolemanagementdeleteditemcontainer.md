<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/directoryrolemanagementdeleteditemcontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# directoryRoleManagementDeletedItemContainer resource type

Namespace: microsoft.graph

Contains soft-deleted custom [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) objects for Microsoft Entra directory role management. Use this container to list, inspect, restore, or permanently delete custom role definitions that have been soft-deleted.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List roleDefinitions](https://learn.microsoft.com/en-us/graph/api/directoryrolemanagementdeleteditemcontainer-list-roledefinitions?view=graph-rest-1.0) | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) collection | List soft-deleted custom role definitions. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the container. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| roleDefinitions | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) collection | The soft-deleted custom role definitions in the directory. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.directoryRoleManagementDeletedItemContainer",
  "id": "String (identifier)"
}
```
