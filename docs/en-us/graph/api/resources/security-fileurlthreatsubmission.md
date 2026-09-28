<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileurlthreatsubmission?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# fileUrlThreatSubmission resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a file threat submission object created when a submission is made using a file URL. This API is reserved and isn't currently supported.

Inherits from [fileThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-filethreatsubmission?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| fileUrl | String | It specifies the URL of the file that needs to be submitted. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.fileUrlThreatSubmission",
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
  "fileName": "String",
  "fileUrl": "String"
}
```
