<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# adminConsentRequestPolicy resource type

Namespace: microsoft.graph

Represents the policy for enabling or disabling the Microsoft Entra admin consent workflow. The admin consent workflow allows users to request access for apps that they wish to use and that require admin authorization before users can use the apps to access organizational data. There is a single **adminConsentRequestPolicy** per tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/adminconsentrequestpolicy-get?view=graph-rest-1.0) | [adminConsentRequestPolicy](https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0) | Read the properties and relationships of an [adminConsentRequestPolicy](https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/adminconsentrequestpolicy-update?view=graph-rest-1.0) | [adminConsentRequestPolicy](https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0) | Update the properties of an [adminConsentRequestPolicy](https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Specifies whether the admin consent request feature is enabled or disabled. Required. |
| notifyReviewers | Boolean | Specifies whether reviewers will receive notifications. Required. |
| remindersEnabled | Boolean | Specifies whether reviewers will receive reminder emails. Required. |
| requestDurationInDays | Int32 | Specifies the duration the request is active before it automatically expires if no decision is applied. |
| reviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | The list of reviewers for the admin consent. Required. |
| version | Int32 | Specifies the version of this policy. When the policy is updated, this version is updated. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.adminConsentRequestPolicy",
  "isEnabled": "Boolean",
  "notifyReviewers": "Boolean",
  "remindersEnabled": "Boolean",
  "requestDurationInDays": "Integer",
  "reviewers": [
    {
      "@odata.type": "microsoft.graph.accessReviewReviewerScope"
    }
  ],
  "version": "Integer"
}
```
