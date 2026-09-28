<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-threatdetectiondetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# threatDetectionDetail resource type

Namespace: microsoft.graph.security

Represents threat analysis information from Microsoft Defender for Office 365, including threat classification, confidence levels, and priority account protection status. It's returned in the **threatDetectionDetails** property of [analyzedEmail](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| confidenceLevel | String | Indicates the confidence level in the threat detection. |
| priorityAccountProtection | String | Indicates if the account has priority protection enabled. |
| threats | String | Lists the detected threats. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.threatDetectionDetail",
  "threats": "String",
  "confidenceLevel": "String",
  "priorityAccountProtection": "String"
}
```
