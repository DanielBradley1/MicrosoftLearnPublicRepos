<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-urlthreatsubmission?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# urlThreatSubmission resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represent a threat submission related to a URL.

This resource is used to submit suspected phishing URLs to Microsoft Defender for Office 365. It can also be used to submit false positive cases that should not have been blocked, such as safe URLs.

Inherits from [threatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-threatsubmission?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-urlthreatsubmission-list?view=graph-rest-beta) | [microsoft.graph.security.urlThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-urlthreatsubmission?view=graph-rest-beta) collection | Get a list of the [urlThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-urlthreatsubmission?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-urlthreatsubmission-post-urlthreats?view=graph-rest-beta) | [microsoft.graph.security.urlThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-urlthreatsubmission?view=graph-rest-beta) | Create a new [urlThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-urlthreatsubmission?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-urlthreatsubmission-get?view=graph-rest-beta) | [microsoft.graph.security.urlThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-urlthreatsubmission?view=graph-rest-beta) | Read the properties and relationships of an [urlThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-urlthreatsubmission?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| webUrl | String | Denotes the webUrl that needs to be submitted. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.urlThreatSubmission",
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
  "webUrl": "String"
}
```
