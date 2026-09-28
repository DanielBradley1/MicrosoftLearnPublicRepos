<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-21 -->

# customAppScope resource type

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a customized RBAC scope object from each RBAC provider. This resource is a subtype of [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-beta), which is a scope defined and understood by a specific application. A custom app scope has its own lifecycle for role assignment objects across various RBAC providers. A custom app scope can also store custom attributes sourced from different RBAC providers.

For example, in the Exchange Online provider, **customAppScope** maps to [management role scope](https://learn.microsoft.com/en-us/exchange/understanding-management-role-scopes-exchange-2013-help) that can be managed separately by Exchange administrators. The CRUD operations for **customAppScope** entities are supported. You can use the ID of a **customAppScope** as the **appScopeId** of a [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta).

The following providers are supported:

- Exchange Online RBAC provider
- Microsoft Defender XDR Unified RBAC provider

Inherits from [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List for Exchange Online and Defender](https://learn.microsoft.com/en-us/graph/api/unifiedrbacapplication-list-customappscopes?view=graph-rest-beta) | [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) collection | Get a list of [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) objects for the Exchange Online or Defender RBAC providers. |
| [List for Defender](https://learn.microsoft.com/en-us/graph/api/unifiedrbacapplicationmultiple-list-customappscopes?view=graph-rest-beta) | [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) collection | Get a list of [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) objects for the Defender RBAC provider. |
| [Create for Exchange Online](https://learn.microsoft.com/en-us/graph/api/unifiedrbacapplication-post-customappscope?view=graph-rest-beta) | [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) | Create a new [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) object for an RBAC provider. |
| [Get for Exchange Online](https://learn.microsoft.com/en-us/graph/api/customappscope-get?view=graph-rest-beta) | [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) | Get the properties of a [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) object for an RBAC provider. |
| [Update for Exchange Online](https://learn.microsoft.com/en-us/graph/api/customappscope-update?view=graph-rest-beta) | None | Update an existing [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) object of an RBAC provider. |
| [Delete for Exchange Online](https://learn.microsoft.com/en-us/graph/api/customappscope-delete?view=graph-rest-beta) | None | Delete a [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) object of an RBAC provider. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customAttributes | [customAppScopeAttributesDictionary](https://learn.microsoft.com/en-us/graph/api/resources/customappscopeattributesdictionary?view=graph-rest-beta) | An open dictionary type that holds workload-specific properties for the scope object. |
| displayName | String | The display name of the app-specific resource represented by the app scope. Provided for display purposes since the **appScopeId** is often an immutable, non-human-readable ID. Read-only. Inherited from [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-beta). |
| id | String | The unique identifier of an app-specific container or resource that represents the scope of the assignment. Usually the immutable ID of the resource. The scope of an assignment determines the set of resources for which the principal has been granted access. Required. Inherited from [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-beta). |
| type | String | The type of app-specific resource represented by the app scope. Provided for display purposes, so a user interface can convey to the user the kind of app-specific resource represented by the app scope. Read-only. Inherited from [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "customAttributes": {
    "@odata.type": "microsoft.graph.customAppScopeAttributesDictionary"
  },
  "displayName": "String",
  "id": "String (identifier)",
  "type": "String"
}
```
