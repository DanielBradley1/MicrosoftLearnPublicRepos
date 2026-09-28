<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# permissionGrantPreApprovalPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A permission grant preapproval policy is used to help administrators granularly control the conditions under which consent can be granted to a specific application.

A permission grant preapproval policy consists of a list of condition sets. An event matches a permission grant preapproval policy if it matches *at least one* of the condition sets in the **conditions** list. Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/policyroot-list-permissiongrantpreapprovalpolicies?view=graph-rest-beta) | [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) collection | Get a list of the [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/policyroot-post-permissiongrantpreapprovalpolicies?view=graph-rest-beta) | [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) | Create a new [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/permissiongrantpreapprovalpolicy-get?view=graph-rest-beta) | [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) | Read the properties and relationships of a [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/permissiongrantpreapprovalpolicy-update?view=graph-rest-beta) | [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) | Update the properties of a [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/permissiongrantpreapprovalpolicy-delete?view=graph-rest-beta) | None | Delete a [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) object. |
| [List assigned to service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-permissiongrantpreapprovalpolicies?view=graph-rest-beta) | [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) collection | Get permissionGrantPreApprovalPolicy assigned to a service principal. |
| [Assign to service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-permissiongrantpreapprovalpolicies?view=graph-rest-beta) | [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) collection | Assign a permissionGrantPreApprovalPolicy to a service principal. |
| [Unassign from service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-permissiongrantpreapprovalpolicies?view=graph-rest-beta) | [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) collection | Remove a permissionGrantPreApprovalPolicy from a service principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conditions | [preApprovalDetail](https://learn.microsoft.com/en-us/graph/api/resources/preapprovaldetail?view=graph-rest-beta) collection | A list of condition sets describing the conditions under which the permission to grant consent for the app has been preapproved. |
| deletedDateTime | DateTimeOffset | Null. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). |
| id | String | The unique identifier for the permission grant preapproval policy. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionGrantPreApprovalPolicy",
  "id": "String (identifier)",
  "deletedDateTime": "String (timestamp)",
  "conditions": [
    {
      "@odata.type": "microsoft.graph.preApprovalDetail"
    }
  ]
}
```
