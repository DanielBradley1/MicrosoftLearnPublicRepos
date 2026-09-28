<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approvalitemviewpoint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# approvalItemViewPoint resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user's roles for an [approvalItem](https://learn.microsoft.com/en-us/graph/api/resources/approvalitem?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| roles | approverRole collection | Collection of roles associated with the requesting user for the approval item. If the owner of the approval item is making the request, the collection of roles includes the role `owner`. If the requesting user was assigned as an approver, the collection includes the role `approver`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approvalItemViewPoint",
  "roles": [
    "String"
  ]
}
```
