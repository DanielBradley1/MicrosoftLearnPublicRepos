<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/assignmentorder?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# assignmentOrder resource type

Namespace: microsoft.graph

Used to define the order of the attributes being collected within a user flow. The order determines how the attribute collection page is displayed when a user signs up using a user flow.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| order | String collection | A list of identityUserFlowAttribute object identifiers that determine the order in which attributes should be collected within a user flow. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.assignmentOrder",
  "order": [
    "String"
  ]
}
```
