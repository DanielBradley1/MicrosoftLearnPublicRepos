<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerorderhintsbyassignee?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-08 -->

# plannerOrderHintsByAssignee resource type

Namespace: microsoft.graph

Contains [ordering hints](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0) for assignees in a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) resource, to indicate the order of the task in Assigned To view of the Task Board. This type is an open type. The properties are the IDs of users assigned to the task, and the values are order hints.

## Properties

Properties of an Open Type can be defined by the client. In this case, the client must provide IDs of users assigned to the task as property names, and a valid [order hint](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0) as the value. Properties can't be removed from this type. The service will automatically remove values as the assignments on the containing [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) are updated.

Example:

```json
{
  "ca2a1df2-e36b-4987-9f6b-0ea462f4eb47": "String",
  "4e98f8f1-bb03-4015-b8e0-19bb370949d8": "String"
}
```
