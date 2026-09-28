<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# appScope resource type

Namespace: microsoft.graph

The scope of a role assignment determines the set of resources for which the principal has access. An app scope is a scope defined and understood by a specific application, unlike directory scopes that are shared scopes stored in the directory and understood by multiple applications.

App scopes support the following principal and scope scenarios:

- A single principal and a single scope
- Multiple principals and multiple scopes.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | string | Provides the display name of the app-specific resource represented by the app scope. Read-only. |
| id | string | ID of an app-specific container or resource representing the scope of the assignment. Usually the immutable ID of the resource. The scope of an assignment determines the set of resources for which the principal is granted access. Required. Read-only. |
| type | String | Describes the type of app-specific resource represented by the app scope. Read-only. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "id": "String (identifier)",
  "type": "String"
}
```
