<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# accessReviewPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Access review policy is a singleton that enables administrators to manage directory-level access review policies. For example, administrators can use the access review policy to enable and disable the ability of group owners to create access reviews on groups that they own.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/accessreviewpolicy-get?view=graph-rest-beta) | [accessReviewPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewpolicy?view=graph-rest-beta) | Read the properties and relationships of an [accessReviewPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewpolicy?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/accessreviewpolicy-update?view=graph-rest-beta) | [accessReviewPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewpolicy?view=graph-rest-beta) | Update the properties of an [accessReviewPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewpolicy?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description for this policy. Read-only. |
| displayName | String | Display name for this policy. Read-only. |
| isGroupOwnerManagementEnabled | Boolean | If `true`, group owners can create and manage access reviews on groups they own. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewPolicy",
  "displayName": "Access Review Policy",
  "description": "Policy contains directory-level access review settings.",
  "isGroupOwnerManagementEnabled": false
}
```
