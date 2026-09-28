<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemailattachment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# analyzedEmailAttachment resource type

Namespace: microsoft.graph.security

Represents an **attachment** to an [analyzed email](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| detonationDetails | [microsoft.graph.security.detonationDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-detonationdetails?view=graph-rest-1.0) | The detonation details of the attachment. |
| fileName | String | The name of the attachment in the email. |
| fileType | String | The type of the attachment in the email. |
| fileSize | Int32 | Size of the file. |
| fileExtension | String | Extension of the file. |
| malwareFamily | String | The threat name associated with the threat type. |
| sha256 | String | The SHA256 file hash of the attachment. |
| threatType | microsoft.graph.security.threatType | The threat type associated with the attachment. The possible values are: `unknown`, `spam`, `malware`, `phishing`, `none`, `unknownFutureValue`. |
| tenantAllowBlockListDetailInfo | String | Details of entries in tenant allow/block list configured by tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.analyzedEmailAttachment",
  "fileName": "String",
  "fileType": "String",
  "fileSize": "Integer",
  "fileExtension": "String",
  "threatType": "String",
  "malwareFamily": "String",
  "tenantAllowBlockListDetailInfo": "String",
  "sha256": "String",
  "detonationDetails": {
    "@odata.type": "microsoft.graph.security.detonationDetails"
  }
}
```
