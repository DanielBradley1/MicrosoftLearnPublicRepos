<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmission?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# emailThreatSubmission resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type to report suspected spam, malware or phishing emails to Microsoft Defender for Office 365. You can also submit false positive cases, that shouldn't have been blocked by Microsoft Defender for Office 365, for example, emails incorrectly categorized as junk or spam.

Inherits from [threatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-threatsubmission?view=graph-rest-beta). Base type of [emailContentThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-emailcontentthreatsubmission?view=graph-rest-beta) and [emailUrlThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-emailurlthreatsubmission?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmission-list?view=graph-rest-beta) | [microsoft.graph.security.emailThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmission?view=graph-rest-beta) collection | Get a list of the [emailThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmission?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmission-post-emailthreats?view=graph-rest-beta) | [microsoft.graph.security.emailThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmission?view=graph-rest-beta) | Create a new [emailThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmission?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmission-get?view=graph-rest-beta) | [microsoft.graph.security.emailThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmission?view=graph-rest-beta) | Read the properties and relationships of an [emailThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmission?view=graph-rest-beta) object. |
| [Review](https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmission-review?view=graph-rest-beta) | None | Review threat submission from end user by administrator. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attackSimulationInfo | [security.attackSimulationInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-attacksimulationinfo?view=graph-rest-beta) | If the email is phishing simulation, this field won't be null. |
| internetMessageId | String | Specifies the internet message ID of the email being submitted. This information is present in the email header. |
| originalCategory | submissionCategory | The original category of the submission. The possible values are: `notJunk`, `spam`, `phishing`, `malware` and `unkownFutureValue`. |
| receivedDateTime | DateTimeOffset | Specifies the date and time stamp when the email was received. |
| recipientEmailAddress | String | Specifies the email address \(in smtp format\) of the recipient who received the email. |
| sender | String | Specifies the email address of the sender. |
| senderIP | String | Specifies the IP address of the sender. |
| subject | String | Specifies the subject of the email. |
| tenantAllowOrBlockListAction | [security.tenantAllowOrBlockListAction](https://learn.microsoft.com/en-us/graph/api/resources/security-tenantalloworblocklistaction?view=graph-rest-beta) | It's used to automatically add allows for the components such as URL, file, sender; which are deemed bad by Microsoft so that similar messages in the future can be allowed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.emailThreatSubmission",
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
  }
}
```
