<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-evaluationresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# evaluationResult resource type

Namespace: microsoft.graph.security.securityCopilot

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The result from a Security Copilot [evaluation](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-evaluation?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | The final content. |
| previewState | microsoft.graph.security.securityCopilot.skillPreviewState | Evaluation skill release information. The possible values are: `ga`, `public`, `private`, `unknownFutureValue`. |
| type | microsoft.graph.security.securityCopilot.evaluationResultType | Evaluation Results types. The possible values are: `unknown`, `success`, `error`, `needAdditionalClaims`, `rejected`, `timedOut`, `capacityExceeded`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.securityCopilot.evaluationResult",
  "content": "String",
  "previewState": "String",
  "type": "String"
}
```
