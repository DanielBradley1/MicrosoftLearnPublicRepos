<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approvalitemrequest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# approvalItemRequest resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a request created for each approver on an [approvalItem](https://learn.microsoft.com/en-us/graph/api/resources/approvalitem?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/approvalitem-list-requests?view=graph-rest-beta) | [approvalItemRequest](https://learn.microsoft.com/en-us/graph/api/resources/approvalitemrequest?view=graph-rest-beta) collection | Get a collection of [approvalItemRequest](https://learn.microsoft.com/en-us/graph/api/resources/approvalitemrequest?view=graph-rest-beta) objects and their properties, associated with an [approvalItem](https://learn.microsoft.com/en-us/graph/api/resources/approvalitem?view=graph-rest-beta). |
| [Get](https://learn.microsoft.com/en-us/graph/api/approvalitemrequest-get?view=graph-rest-beta) | [approvalItemRequest](https://learn.microsoft.com/en-us/graph/api/resources/approvalitemrequest?view=graph-rest-beta) | Read the properties and relationships of an [approvalItemRequest](https://learn.microsoft.com/en-us/graph/api/resources/approvalitemrequest?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approver | [approvalIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/approvalidentityset?view=graph-rest-beta) | The identity set of the principal assigned to this request. |
| createdDateTime | DateTimeOffset | Creation date and time for the request. |
| isReassigned | Boolean | Indicates whether a request was reassigned. |
| reassignedFrom | [approvalIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/approvalidentityset?view=graph-rest-beta) | The identity set of the principal who reassigned the request. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approvalItemRequest",
  "createdDateTime": "String (timestamp)",
  "approver": {
    "@odata.type": "microsoft.graph.approvalIdentitySet"
  },
  "reassignedFrom": {
    "@odata.type": "microsoft.graph.approvalIdentitySet"
  },
  "isReassigned": "Boolean"
}
```
