<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approvalsolution?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# approvalSolution resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the provisioning status of the approval solution for a tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/approvalsolution-get?view=graph-rest-beta) | [approvalSolution](https://learn.microsoft.com/en-us/graph/api/resources/approvalsolution?view=graph-rest-beta) | Read the properties and relationships of an [approvalSolution](https://learn.microsoft.com/en-us/graph/api/resources/approvalsolution?view=graph-rest-beta) object. |
| [Provision](https://learn.microsoft.com/en-us/graph/api/approvalsolution-provision?view=graph-rest-beta) | None | Provisions an approval solution instance on behalf of the tenant. |
| [List approval items](https://learn.microsoft.com/en-us/graph/api/approvalsolution-list-approvalitems?view=graph-rest-beta) | [approvalItem](https://learn.microsoft.com/en-us/graph/api/resources/approvalitem?view=graph-rest-beta) collection | Get the approvalItem resources from the approvalItems navigation property. |
| [Create approval item](https://learn.microsoft.com/en-us/graph/api/approvalsolution-post-approvalitems?view=graph-rest-beta) | [approvalItem](https://learn.microsoft.com/en-us/graph/api/resources/approvalitem?view=graph-rest-beta) | Create a new approvalItem object. |
| [Get approval operation](https://learn.microsoft.com/en-us/graph/api/approvaloperation-get?view=graph-rest-beta) | [approvalOperation](https://learn.microsoft.com/en-us/graph/api/resources/approvaloperation?view=graph-rest-beta) | Get an approvalOperation object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| provisioningStatus | provisionState | The approval provisioning status for a tenant on an environment. The possible values are: `notProvisioned`, `provisioningInProgress`, `provisioningFailed`, `provisioningCompleted`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| approvalItems | [approvalItem](https://learn.microsoft.com/en-us/graph/api/resources/approvalitem?view=graph-rest-beta) collection | A collection of approval items. |
| approvalOperations | [approvalOperation](https://learn.microsoft.com/en-us/graph/api/resources/approvaloperation?view=graph-rest-beta) collection | A collection of approval operations. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approvalSolution",
  "provisioningStatus": "String"
}
```
