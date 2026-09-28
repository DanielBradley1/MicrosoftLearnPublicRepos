<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/availableaccesspackage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# availableAccessPackage resource type

Namespace: microsoft.graph

In [Microsoft Entra Entitlement Management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an available access package represents basic access package information \(id, displayName, description\) that is exposed to end users for [suggestions](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestion?view=graph-rest-1.0) and [resource discovery](https://learn.microsoft.com/en-us/graph/api/availableaccesspackage-list-resourcerolescopes?view=graph-rest-1.0) purposes.

This resource provides a simplified view of access packages that can be used in scenarios where end users need to browse available packages without requiring full access package details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List resourceRoleScopes](https://learn.microsoft.com/en-us/graph/api/availableaccesspackage-list-resourcerolescopes?view=graph-rest-1.0) | [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-1.0) collection | Retrieve the resource role scopes for an available access package. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the access package. |
| displayName | String | The display name of the access package. |
| id | String | Identifier of the access package. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| resourceRoleScopes | [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-1.0) collection | The resource role scopes associated with this available access package. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.availableAccessPackage",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String"
}
```
