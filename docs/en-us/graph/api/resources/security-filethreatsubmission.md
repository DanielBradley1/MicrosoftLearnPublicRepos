<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-filethreatsubmission?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# fileThreatSubmission resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a threat submission related to a file. It's used to submit suspected malware email attachments to Microsoft Defender for Office 365. It could also be used to submit false positive cases that shouldn't have been blocked by Microsoft Defender for Office 365, for example, a safe email attachment.

Currently, file threat submission is routed to Microsoft Defender for Office 365. In future, it may be routed to Microsoft Defender for Endpoint. This is a unified interface for file threat submission no matter where it's routed to.

This is an abstract type. Inherits from [threatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-threatsubmission?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-filethreatsubmission-list?view=graph-rest-beta) | [microsoft.graph.security.fileThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-filethreatsubmission?view=graph-rest-beta) collection | Get a list of the [fileThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-filethreatsubmission?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-filethreatsubmission-post-filethreats?view=graph-rest-beta) | [microsoft.graph.security.fileThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-filethreatsubmission?view=graph-rest-beta) | Create a new [fileThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-filethreatsubmission?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-filethreatsubmission-get?view=graph-rest-beta) | [microsoft.graph.security.fileThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-filethreatsubmission?view=graph-rest-beta) | Read the properties and relationships of a [fileThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-filethreatsubmission?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| fileName | String | It specifies the file name to be submitted. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.fileThreatSubmission",
  "id": "String (identifier)",
  "tenantId": "String",
  "createdDateTime": "String (timestamp)",
  "contentType": "String",
  "category": "String",
  "source": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.security.submissionUserIdentity"
  },
  "status": "String",
  "result": {
    "@odata.type": "microsoft.graph.security.submissionResult"
  },
  "adminReview": {
    "@odata.type": "microsoft.graph.security.submissionAdminReview"
  },
  "clientSource": "String",
  "fileName": "String"
}
```
