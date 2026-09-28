<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-compromiseindicator?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# compromiseIndicator resource type

Namespace: microsoft.graph.security

Represents an indicator and its associated verdict that suggests whether an email is compromised. The resource combines specific indicators found in the email with categorized verdicts to help identify potential security threats like malware, phishing attempts, or spam. It is returned in the **compromiseIndicators** property of [detonationDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-detonationdetails?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | String | Indicator. |
| verdict | [microsoft.graph.security.verdictCategory](#verdictcategory-values) | The possible values are: `none`, `malware`, `phish`, `siteUnavailable`, `spam`, `decryptionFailed`, `unsupportedUriScheme`, `unsupportedFileType`, `undefined`, `unknownFutureValue`. |

### verdictCategory values

| Member |
| :--- |
| none |
| malware |
| phish |
| siteUnavailable |
| spam |
| decryptionFailed |
| unsupportedUriScheme |
| unsupportedFileType |
| undefined |
| unknownFutureValue |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.compromiseIndicator",
  "verdict": "String",
  "value": "String"
}
```
