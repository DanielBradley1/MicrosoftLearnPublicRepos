<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemailurl?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# analyzedEmailUrl resource type

Namespace: microsoft.graph.security

Represents information about URLs found in an [analyzed email](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| detectionMethod | String | The method used to detect threats in the URL. |
| detonationDetails | [microsoft.graph.security.detonationDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-detonationdetails?view=graph-rest-1.0) | Detonation data associated with the URL. |
| tenantAllowBlockListDetailInfo | String | Details of entries in tenant allow/block list configured by tenant. |
| threatType | microsoft.graph.security.threatType | The type of threat associated with the URL. The possible values are: `unknown`, `spam`, `malware`, `phishing`, `none`, `unknownFutureValue`. |
| url | String | The URL that is found in the email. This is full URL string, including query parameters. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.analyzedEmailUrl",
  "url": "String",
  "threatType": "String",
  "detectionMethod": "String",
  "tenantAllowBlockListDetailInfo": "String",
  "detonationDetails": {
    "@odata.type": "microsoft.graph.security.detonationDetails"
  }
}
```
