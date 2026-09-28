<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfilterevaluationsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# assignmentFilterEvaluationSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represent result summary for assignment filter evaluation

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentFilterId | String | Unique identifier for the assignment filter object |
| assignmentFilterLastModifiedDateTime | DateTimeOffset | The time the assignment filter was last modified. |
| assignmentFilterDisplayName | String | The admin defined name for assignment filter. |
| assignmentFilterPlatform | [devicePlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceplatformtype?view=graph-rest-beta) | The platform for which this assignment filter is created. Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidAOSP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`, `windowsMobileApplicationManagement`. |
| evaluationResult | [assignmentFilterEvaluationResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfilterevaluationresult?view=graph-rest-beta) | Assignment filter evaluation result. Possible values are: `unknown`, `match`, `notMatch`, `inconclusive`, `failure`, `notEvaluated`. |
| evaluationDateTime | DateTimeOffset | The time assignment filter was evaluated. |
| assignmentFilterType | [deviceAndAppManagementAssignmentFilterType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmentfiltertype?view=graph-rest-beta) | Indicate filter type either include or exclude. Possible values are: `none`, `include`, `exclude`. |
| assignmentFilterTypeAndEvaluationResults | [assignmentFilterTypeAndEvaluationResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfiltertypeandevaluationresult?view=graph-rest-beta) collection | A collection of filter types and their corresponding evaluation results. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.assignmentFilterEvaluationSummary",
  "assignmentFilterId": "String",
  "assignmentFilterLastModifiedDateTime": "String (timestamp)",
  "assignmentFilterDisplayName": "String",
  "assignmentFilterPlatform": "String",
  "evaluationResult": "String",
  "evaluationDateTime": "String (timestamp)",
  "assignmentFilterType": "String",
  "assignmentFilterTypeAndEvaluationResults": [
    {
      "@odata.type": "microsoft.graph.assignmentFilterTypeAndEvaluationResult",
      "assignmentFilterType": "String",
      "evaluationResult": "String"
    }
  ]
}
```
