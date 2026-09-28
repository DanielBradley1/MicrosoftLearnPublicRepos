<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approvalitemresponse?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# approvalItemResponse resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a response to an approval item request.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/approvalitem-list-responses?view=graph-rest-beta) | [approvalItemResponse](https://learn.microsoft.com/en-us/graph/api/resources/approvalitemresponse?view=graph-rest-beta) collection | Get a list of the [approvalItemResponse](https://learn.microsoft.com/en-us/graph/api/resources/approvalitemresponse?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/approvalitem-post-responses?view=graph-rest-beta) | [approvalItemResponse](https://learn.microsoft.com/en-us/graph/api/resources/approvalitemresponse?view=graph-rest-beta) | Create a new [approvalItemResponse](https://learn.microsoft.com/en-us/graph/api/resources/approvalitemresponse?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/approvalitemresponse-get?view=graph-rest-beta) | [approvalItemResponse](https://learn.microsoft.com/en-us/graph/api/resources/approvalitemresponse?view=graph-rest-beta) | Read the properties and relationships of an [approvalItemResponse](https://learn.microsoft.com/en-us/graph/api/resources/approvalitemresponse?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| comments | String | The comment made by the approver. |
| createdBy | [approvalIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/approvalidentityset?view=graph-rest-beta) | The identity set of the approver. |
| createdDateTime | DateTimeOffset | Creation date and time of the response. |
| owners | [approvalIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/approvalidentityset?view=graph-rest-beta) collection | The identity set of the principal who owns the approval item. |
| response | String | Approver response based on the response options. The default response options are "Approved" and "Rejected". The approval item creator can also define custom response options during [approval item creation](https://learn.microsoft.com/en-us/graph/api/approvalsolution-post-approvalitems?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approvalItemResponse",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.approvalIdentitySet"
  },
  "comments": "String",
  "response": "String",
  "owners": [
    {
      "@odata.type": "microsoft.graph.approvalIdentitySet"
    }
  ]
}
```
