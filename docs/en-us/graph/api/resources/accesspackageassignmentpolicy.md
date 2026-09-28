<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# accessPackageAssignmentPolicy resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package assignment policy specifies the policy by which subjects can request or be assigned an access package via an access package assignment. An access package can have zero or more policies. When a request from a subject is received, the subject is matched against each policy to find the policy \(if any\) with **requestorSettings** that include that subject. The policy then determines whether the request requires approval, the duration of the access package assignment, and whether the assignment needs regular reviews.

To assign a user to an access package, [create an accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-assignmentrequests?view=graph-rest-1.0) which references the access package and access package assignment policy.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-assignmentpolicies?view=graph-rest-1.0) | [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) collection | Get a list of the [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-assignmentpolicies?view=graph-rest-1.0) | [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) | Create a new [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-1.0) | [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) | Read the properties and relationships of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-update?view=graph-rest-1.0) | [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) | Update the properties of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-delete?view=graph-rest-1.0) | None | Deletes an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessPackageNotificationSettings | [accessPackageNotificationSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagenotificationsettings?view=graph-rest-1.0) | Represents the settings for email notifications for requests to an access package. |
| allowedTargetScope | allowedTargetScope | Principals that can be assigned the access package through this policy. The possible values are: `notSpecified`, `specificDirectoryUsers`, `specificConnectedOrganizationUsers`, `specificDirectoryServicePrincipals`, `allMemberUsers`, `allDirectoryUsers`, `allDirectoryServicePrincipals`, `allConfiguredConnectedOrganizationUsers`, `allExternalUsers`, `allDirectoryAgentIdentities`, `unknownFutureValue`. |
| automaticRequestSettings | [accessPackageAutomaticRequestSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageautomaticrequestsettings?view=graph-rest-1.0) | This property is only present for an auto assignment policy; if absent, this is a request-based policy. |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | The description of the policy. |
| displayName | String | The display name of the policy. |
| expiration | [expirationPattern](https://learn.microsoft.com/en-us/graph/api/resources/expirationpattern?view=graph-rest-1.0) | The expiration date for assignments created in this policy. |
| id | String | Read-only. |
| modifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| requestApprovalSettings | [accessPackageAssignmentApprovalSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentapprovalsettings?view=graph-rest-1.0) | Specifies the settings for approval of requests for an access package assignment through this policy. For example, if approval is required for new requests. |
| requestorSettings | [accessPackageAssignmentRequestorSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestorsettings?view=graph-rest-1.0) | Provides additional settings to select who can create a request for an access package assignment through this policy, and what they can include in their request. |
| reviewSettings | [accessPackageAssignmentReviewSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentreviewsettings?view=graph-rest-1.0) | Settings for access reviews of assignments through this policy. |
| specificAllowedTargets | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | The principals that can be assigned access from an access package through this policy. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessPackage | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) | Access package containing this policy. Read-only. Supports `$expand`. |
| catalog | [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) | Catalog of the access package containing this policy. Read-only. |
| customExtensionStageSettings | [customExtensionStageSetting](https://learn.microsoft.com/en-us/graph/api/resources/customextensionstagesetting?view=graph-rest-1.0) collection | The collection of stages when to execute one or more custom access package workflow extensions. Supports `$expand`. |
| questions | [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0) collection | Questions that are posed to the requestor. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentPolicy",
  "allowedTargetScope": "String",
  "automaticRequestSettings": {
    "@odata.type": "microsoft.graph.accessPackageAutomaticRequestSettings"
  },
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "expiration": {
    "@odata.type": "microsoft.graph.expirationPattern"
  },
  "id": "String (identifier)",
  "modifiedDateTime": "String (timestamp)",
  "requestorSettings": {
    "@odata.type": "microsoft.graph.accessPackageAssignmentRequestorSettings"
  },
  "questions": [
    {
      "@odata.type": "microsoft.graph.accessPackageQuestion"
    }
  ],
  "requestApprovalSettings": {
    "@odata.type": "microsoft.graph.accessPackageAssignmentApprovalSettings"
  },
  "reviewSettings": {
    "@odata.type": "microsoft.graph.accessPackageAssignmentReviewSettings"
  },
    "accessPackageNotificationSettings": {
    "@odata.type": "microsoft.graph.accessPackageNotificationSettings"
  },
  "specificAllowedTargets": [
    {
      "@odata.type": "microsoft.graph.singleUser"
    },
  ]
 
}
```
