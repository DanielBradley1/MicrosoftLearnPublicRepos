<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# keyValuePair resource type

Namespace: microsoft.graph

Key-value pair for action parameters. This object is configured in the following resources:

- **synchronizationJobSettings** property of [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0)
- **arguments** property of [task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) \(Lifecycle Workflows\)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name for this key-value pair |
| value | String | Value for this key-value pair |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "name": "String",
  "value": "String"
}
```
