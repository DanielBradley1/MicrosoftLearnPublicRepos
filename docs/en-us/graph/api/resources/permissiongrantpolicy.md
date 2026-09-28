<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# permissionGrantPolicy resource type

Namespace: microsoft.graph

A permission grant policy is used to specify the conditions under which consent can be granted.

A permission grant policy consists of a list of **includes** condition sets, and a list of **excludes** condition sets. For an event to match a permission grant policy, it must match *at least one* of the **includes** conditions sets, and *none* of the **excludes** condition sets.

For more information, see [Manage app consent policies](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/manage-app-consent-policies).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/permissiongrantpolicy-list?view=graph-rest-1.0) | [permissionGrantPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpolicy?view=graph-rest-1.0) collection | Retrieve a list of permissionGrantPolicy objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/permissiongrantpolicy-post-permissiongrantpolicies?view=graph-rest-1.0) | [permissionGrantPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpolicy?view=graph-rest-1.0) | Creates a new permissionGrantPolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/permissiongrantpolicy-get?view=graph-rest-1.0) | [permissionGrantPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpolicy?view=graph-rest-1.0) | Read properties and relationships of permissionGrantPolicy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/permissiongrantpolicy-update?view=graph-rest-1.0) | [permissionGrantPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpolicy?view=graph-rest-1.0) | Update permissionGrantPolicy object. |
| **Include condition sets** |  |  |
| [List includes](https://learn.microsoft.com/en-us/graph/api/permissiongrantpolicy-list-includes?view=graph-rest-1.0) | [permissionGrantConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantconditionset?view=graph-rest-1.0) collection | Get the condition sets that are *included* in this permission grant policy. |
| [Create in includes](https://learn.microsoft.com/en-us/graph/api/permissiongrantpolicy-post-includes?view=graph-rest-1.0) | [permissionGrantConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantconditionset?view=graph-rest-1.0) | Add a condition set that is *included* from this permission grant policy. |
| [Delete from includes](https://learn.microsoft.com/en-us/graph/api/permissiongrantpolicy-delete-includes?view=graph-rest-1.0) | None | Remove a condition set that is *excluded* from this permission grant policy. |
| **Exclude condition sets** |  |  |
| [List excludes](https://learn.microsoft.com/en-us/graph/api/permissiongrantpolicy-list-excludes?view=graph-rest-1.0) | [permissionGrantConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantconditionset?view=graph-rest-1.0) collection | Get the condition sets that are *excluded* in this permission grant policy. |
| [Create in excludes](https://learn.microsoft.com/en-us/graph/api/permissiongrantpolicy-post-excludes?view=graph-rest-1.0) | [permissionGrantConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantconditionset?view=graph-rest-1.0) | Add a condition set that is *excluded* from this permission grant policy. |
| [Delete from excludes](https://learn.microsoft.com/en-us/graph/api/permissiongrantpolicy-delete-excludes?view=graph-rest-1.0) | None | Remove a condition set that is *excluded* from this permission grant policy. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name for the permission grant policy. |
| description | String | The description for the permission grant policy. |
| excludes | [permissionGrantConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantconditionset?view=graph-rest-1.0) collection | Condition sets that are *excluded* in this permission grant policy. Automatically expanded on `GET`. |
| id | String | The unique identifier for the permission grant policy. The **id** prefix `microsoft-` is reserved for built-in permission grant policies, and may not be used in a custom permission grant policy. Only letters, numbers, hyphens \(`-`\) and underscores \(`_`\) are allowed. Key. Not nullable. Required on create. Immutable. |
| includes | [permissionGrantConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantconditionset?view=graph-rest-1.0) collection | Condition sets that are *included* in this permission grant policy. Automatically expanded on `GET`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| excludes | [permissionGrantConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantconditionset?view=graph-rest-1.0) collection | Condition sets that are *excluded* in this permission grant policy. This navigation is automatically expanded on GET. |
| includes | [permissionGrantConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantconditionset?view=graph-rest-1.0) collection | Condition sets that are *included* in this permission grant policy. This navigation is automatically expanded on GET. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string (identifier)",
  "displayName": "string",
  "description": "string",
  "includes": "collection(microsoft.graph.permissionGrantConditionSet)",
  "excludes": "collection(microsoft.graph.permissionGrantConditionSet)"
}
```
