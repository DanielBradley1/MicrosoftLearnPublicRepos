<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approval?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# approval resource type

Namespace: microsoft.graph

Represents the approval object for decisions associated with a request.

In [PIM for Groups](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagement-for-groups-api-overview?view=graph-rest-1.0), the approval object for decisions to approve or deny requests to activate group membership or ownership.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/approval-get?view=graph-rest-1.0) | [approval](https://learn.microsoft.com/en-us/graph/api/resources/approval?view=graph-rest-1.0) | Retrieve the properties of an **approval** object in entitlement management and PIM. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/approval-filterbycurrentuser?view=graph-rest-1.0) | [approval](https://learn.microsoft.com/en-us/graph/api/resources/approval?view=graph-rest-1.0) collection | Retrieve the **approval** objects for an approver in entitlement management and PIM. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier of the approval decision.  <br><br><br><li>In PIM for Groups, it&#39;s the same identifier as the identifier of the <a href="https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0" data-linktype="relative-path">assignment schedule request</a>.</li> |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| stages | [approvalStage](https://learn.microsoft.com/en-us/graph/api/resources/approvalstage?view=graph-rest-1.0) collection | A collection of stages in the approval decision. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approval",
  "id": "String (identifier)",
  "stages": [{
        "@odata.type": "#microsoft.graph.approvalStage"
    }]
}
```
