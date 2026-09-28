<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-cancelrunsscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# cancelRunsScope resource type

Namespace: microsoft.graph.identityGovernance

Defines a set of [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) runs to cancel when using the [cancelProcessing](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-cancelprocessing?view=graph-rest-1.0) action. Only runs that are currently in `queued` or `inProgress` status can be cancelled.

Inherits from [cancelScope](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-cancelscope?view=graph-rest-1.0).

## Properties

None.

## Relationships

| Property | Type | Description |
| :--- | :--- | :--- |
| runs | [microsoft.graph.identityGovernance.run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) collection | The workflow runs to cancel. Currently limited to 1 run per request. Required. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.cancelRunsScope"
}
```
