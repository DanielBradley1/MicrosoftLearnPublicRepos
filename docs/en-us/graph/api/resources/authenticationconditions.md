<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# authenticationConditions resource type

Namespace: microsoft.graph

The conditions on which an authenticationEventListener should trigger.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applications | [authenticationConditionsApplications](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditionsapplications?view=graph-rest-1.0) | Applications which trigger a custom authentication extension. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationConditions",
  "applications": {
    "@odata.type": "microsoft.graph.authenticationConditionsApplications"
  }
}
```
