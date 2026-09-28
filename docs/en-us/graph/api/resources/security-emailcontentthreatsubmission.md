<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-emailcontentthreatsubmission?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# emailContentThreatSubmission resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a threat submission related to the content of an email, and is created when the submission is made using email file content.

Inherits from [emailThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmission?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| fileContent | String | Base64 encoded file content. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.emailContentThreatSubmission",
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
  "recipientEmailAddress": "String",
  "internetMessageId": "String",
  "subject": "String",
  "sender": "String",
  "senderIP": "String",
  "receivedDateTime": "String (timestamp)",
  "originalCategory": "String",
  "attackSimulationInfo": {
    "@odata.type": "microsoft.graph.security.attackSimulationInfo"
  },
  "tenantAllowOrBlockListAction": {
    "@odata.type": "microsoft.graph.security.tenantAllowOrBlockListAction"
  },
  "fileContent": "String"
}
```
