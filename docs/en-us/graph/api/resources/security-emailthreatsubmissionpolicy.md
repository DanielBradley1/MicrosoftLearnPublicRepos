<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# emailThreatSubmissionPolicy resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the guidelines of an organization to report potential threats and spam messages. It's used for customizing your organization's end user threat submission experience when reporting potential threats and spam in Microsoft Outlook.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmissionpolicy-list?view=graph-rest-beta) | [microsoft.graph.security.emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) collection | Get a list of the [emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmissionpolicy-post-emailthreatsubmissionpolicies?view=graph-rest-beta) | [microsoft.graph.security.emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) | Create a new [emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmissionpolicy-get?view=graph-rest-beta) | [microsoft.graph.security.emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) | Read the properties and relationships of an [emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmissionpolicy-update?view=graph-rest-beta) | None | Update the properties of an [emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmissionpolicy-delete?view=graph-rest-beta) | None | Deletes an [emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customizedNotificationSenderEmailAddress | String | Specifies the email address of the sender from which email notifications will be sent to end users to inform them whether an email is spam, phish or clean. The default value is `null`. Optional for creation. |
| customizedReportRecipientEmailAddress | String | Specifies the destination where the reported messages from end users land whenever they report something as phish, junk or not junk. The default value is `null`. Optional for creation. |
| id | String | Only one id is supported. The default value is `DefaultReportSubmissionPolicy`. |
| isAlwaysReportEnabledForUsers | Boolean | Indicates whether end users can report a message as spam, phish or junk directly without a confirmation\(popup\). The default value is `true`. Optional for creation. |
| isAskMeEnabledForUsers | Boolean | Indicates whether end users can confirm using a popup before reporting messages as spam, phish or not junk. The default value is `true`. Optional for creation. |
| isCustomizedMessageEnabled | Boolean | Indicates whether the email notifications sent to end users to inform them if an email is a phish mail, spam or junk is customized or not. The default value is `false`. Optional for creation. |
| isCustomizedMessageEnabledForPhishing | Boolean | If enabled, customized message only shows when email is reported as phishing. The default value is `false`. Optional for creation. |
| isCustomizedNotificationSenderEnabled | Boolean | Indicates whether to use the sender email address set using customizedNotificationSenderEmailAddress for sending email notifications to end users. The default value is `false`. Optional for creation. |
| isNeverReportEnabledForUsers | Boolean | Indicates whether end users can move the message from one folder to another based on the action of spam, phish or not junk without actually reporting it. The default value is `true`. Optional for creation. |
| isOrganizationBrandingEnabled | Boolean | Indicates whether the branding logo should be used in the email notifications sent to end users. The default value is `false`. Optional for creation. |
| isReportFromQuarantineEnabled | Boolean | Indicates whether end users can submit from the quarantine page. The default value is `true`. Optional for creation. |
| isReportToCustomizedEmailAddressEnabled | Boolean | Indicates whether emails reported by end users should be sent to the custom mailbox configured using customizedReportRecipientEmailAddress. The default value is `false`. Optional for creation. |
| isReportToMicrosoftEnabled | Boolean | If enabled, the email is sent to Microsoft for analysis. The default value is `false`. Required for creation. |
| isReviewEmailNotificationEnabled | Boolean | Indicates whether an email notification is sent to the end user who reported the email when it has been reviewed by the admin. The default value is `false`. Optional for creation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.emailThreatSubmissionPolicy",
  "id": "String (identifier)",
  "isReportToMicrosoftEnabled": "Boolean",
  "isReportToCustomizedEmailAddressEnabled": "Boolean",
  "isAskMeEnabledForUsers": "Boolean",
  "isAlwaysReportEnabledForUsers": "Boolean",
  "isNeverReportEnabledForUsers": "Boolean",
  "isCustomizedMessageEnabledForPhishing": "Boolean",
  "isCustomizedMessageEnabled": "Boolean",
  "customizedReportRecipientEmailAddress": "String",
  "isReviewEmailNotificationEnabled": "Boolean",
  "isCustomizedNotificationSenderEnabled": "Boolean",
  "isOrganizationBrandingEnabled": "Boolean",
  "customizedNotificationSenderEmailAddress": "String",
  "isReportFromQuarantineEnabled": "Boolean"
}
```
