<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-detonationdetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# detonationDetails resource type

Namespace: microsoft.graph.security

Represents detonation details specific to email attachments and URLs. These details include the detonation chain, detonation summary, and observed behavior details to help customers understand the reason the attachment or URL is deemed malicious and detonated. It's returned in the **detonationDetails** property of [analyzedEmailAttachment](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemailattachment?view=graph-rest-1.0) and [analyzedEmailUrl](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemailurl?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| analysisDateTime | DateTimeOffset | The time of detonation. |
| compromiseIndicators | [microsoft.graph.security.compromiseIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-compromiseindicator?view=graph-rest-1.0) collection | Represents indicators and its associated verdict that suggests whether an email is compromised. |
| detonationChain | [microsoft.graph.security.detonationChain](https://learn.microsoft.com/en-us/graph/api/resources/security-detonationchain?view=graph-rest-1.0) | The chain of detonation. |
| detonationObservables | [microsoft.graph.security.detonationObservables](https://learn.microsoft.com/en-us/graph/api/resources/security-detonationobservables?view=graph-rest-1.0) | All observables in the detonation tree. |
| detonationVerdict | String | The verdict of the detonation. |
| detonationVerdictReason | String | The reason for the verdict of the detonation. |
| detonationBehaviourDetailsV2 | String | Shows the exact events that took place during detonation, and problematic or benign observations that contain URLs, IPs, domains, and files that were found during detonation in a JSON format. |
| detonationScreenshotUri | String | Show any screenshots that were captured during detonation. No screenshots are captured if the URL opens into a link that directly downloads a file. However, you see the downloaded file in the detonation chain. |
| entityMetadata | String | Additional metadata about the entity in JSON format. |
| mitreTechniques | String | The attack techniques, as aligned with the MITRE ATT&CK framework. |
| staticAnalysis | String | The results of static analysis performed on the file or URL. |
| submissionSource | String | The source of the submission. |
| detonationBehaviourDetails \(deprecated\) | [microsoft.graph.security.detonationBehaviourDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-detonationbehaviourdetails?view=graph-rest-1.0) | Shows the exact events that took place during detonation, and problematic or benign observations that contain URLs, IPs, domains, and files that were found during detonation. This property is deprecated and still stop returning data in March 2026. Use the **detonationBehaviourDetailsV2** property instead. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.detonationDetails",
  "analysisDateTime": "String (timestamp)",
  "detonationVerdict": "String",
  "detonationVerdictReason": "String",
  "detonationChain": {
    "@odata.type": "microsoft.graph.security.detonationChain"
  },
  "detonationObservables": {
    "@odata.type": "microsoft.graph.security.detonationObservables"
  },
  "detonationBehaviourDetailsV2": "String",
  "detonationScreenshotUri": "String",
  "compromiseIndicators": [
    {
      "@odata.type": "microsoft.graph.security.compromiseIndicator"
    }
  ],
  "submissionSource": "String",
  "entityMetadata": "String",
  "staticAnalysis": "String",
  "mitreTechniques": "String",
  "detonationBehaviourDetails": {
    "@odata.type": "microsoft.graph.security.detonationBehaviourDetails"
  }
}
```
