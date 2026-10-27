<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# privilegedAccessRoot resource type

Namespace: microsoft.graph

Represents the entry point for resources related to Privileged Identity Management \(PIM\).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List custom extensions](https://learn.microsoft.com/en-us/graph/api/privilegedaccessroot-list-customextensions?view=graph-rest-1.0) | [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0) collection | Get a list of PIM custom extensions. |
| [Create custom extension](https://learn.microsoft.com/en-us/graph/api/privilegedaccessroot-post-customextensions?view=graph-rest-1.0) | [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0) | Create a PIM custom extension. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier for an object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customExtensions | [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0) collection | The custom extensions configured for PIM role management operations. |
| group | [privilegedAccessGroup](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroup?view=graph-rest-1.0) | A group that's governed through Privileged Identity Management \(PIM\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegedAccessRoot",
  "id": "String (identifier)"
}
```
