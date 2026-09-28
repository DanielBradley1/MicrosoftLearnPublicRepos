<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/provisioningstep?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# provisioningStep resource type

Namespace: microsoft.graph

Describes the steps taken to perform an action. This object is configured in the **provisioningSteps** property of [provisioningObjectSummary](https://learn.microsoft.com/en-us/graph/api/resources/provisioningobjectsummary?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Summary of what occurred during the step. |
| details | [detailsInfo](https://learn.microsoft.com/en-us/graph/api/resources/detailsinfo?view=graph-rest-1.0) | Details of what occurred during the step. |
| name | String | Name of the step. |
| provisioningStepType | provisioningStepType | Type of step. The possible values are: `import`, `scoping`, `matching`, `processing`, `referenceResolution`, `export`, `unknownFutureValue`. |
| status | provisioningResult | Status of the step. The possible values are: `success`, `warning`, `failure`, `skipped`, `unknownFutureValue`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "details": {
    "@odata.type": "microsoft.graph.detailsInfo"
  },
  "name": "String",
  "provisioningStepType": "String",
  "status": "String"
}
```
