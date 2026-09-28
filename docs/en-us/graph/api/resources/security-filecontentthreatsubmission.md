<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-filecontentthreatsubmission?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# fileContentThreatSubmission resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a threat submission object created when the submission is made using the content of a file.

Inherits from [fileThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-filethreatsubmission?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| fileContent | String | It specifies the file content in base 64 format. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.fileContentThreatSubmission",
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
  "fileContent": "String"
}
```
