<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/evaluationerrordetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# evaluationErrorDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the structured reason for the **inspectionIncompleteReason** property of [evaluationIncompleteActivityMetadata](https://learn.microsoft.com/en-us/graph/api/resources/evaluationincompleteactivitymetadata?view=graph-rest-beta) when a policy evaluation couldn't be completed.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errorCategory | [evaluationErrorCategory](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#evaluationerrorcategory-values) | The high-level category of the error. Required. The possible values are: `unknown`, `systemLimit`, `systemError`, `enforcementError`, `unknownFutureValue`. |
| errorMessage | String | A message that describes the error. Required. |
| errorType | [evaluationErrorType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#evaluationerrortype-values) | The specific reason the evaluation couldn't be completed. Required. The possible values are: `unsupportedFile`, `passwordProtectedFile`, `fileTooLarge`, `archiveSizeTooLarge`, `textExceedsMceThreshold`, `partiallyScannedArchive`, `partialImageExtraction`, `imageOcrPartialResult`, `ocrProcessingFailure`, `ocrQuotaExhausted`, `classificationServiceError`, `sitExtractionFailure`, `textExtractionFailure`, `archiveTextExtractionError`, `missingOrInvalidConfiguration`, `agentFailure`, `enforcementTimeout`, `osOverride`, `processNonExistent`, `other`, `serviceTimeout`, `serviceError`, `serviceUnavailable`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.evaluationErrorDetail",
  "errorCategory": "String",
  "errorMessage": "String",
  "errorType": "String"
}
```
