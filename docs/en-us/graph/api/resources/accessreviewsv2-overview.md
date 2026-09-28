<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Overview of access reviews APIs

Namespace: microsoft.graph

Use [Microsoft Entra access reviews](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview) to configure one-time or recurring access reviews for attestation of a principal's right to access Microsoft Entra resources. The principals are users or applications \(service principals\). The Microsoft Entra resources include groups, applications \(service principals\), access packages, and privileged roles. Access reviews is a feature of Microsoft Entra ID Governance.

Typical customer scenarios for access reviews include:

- Customers can review and certify guest user access to groups through group memberships. Reviewers can use the insights that are provided to efficiently decide whether guests should have continued access.
- Customers can review and certify employee access to Microsoft Entra resources.
- Customers can review and audit assignments to Microsoft Entra ID privileged roles. This supports organizations in the management of privileged access.

The tenant where an access review is being created or managed via the API must have sufficient purchased or trial licenses. For more information about the license requirements, see [Access reviews license requirements](https://learn.microsoft.com/en-us/azure/active-directory/governance/access-reviews-overview#license-requirements).

Note

This article describes how to export personal data from a device or service. These steps can be used to support your obligations under the General Data Protection Regulation \(GDPR\). Authorized tenant admins can use Microsoft Graph to correct, update, or delete identifiable information about end users, including customer and employee user profiles or personal data, such as a user's name, work title, address, or phone number, in your [Microsoft Entra ID](https://www.microsoft.com/security/business/identity-access/microsoft-entra-id) environment.

## Methods

The following table lists the methods that you can use to interact with access review-related resources.

| Method | Return type | Description |
| :--- | :--- | :--- |
| **Schedule definitions** |  |  |
| [List definitions](https://learn.microsoft.com/en-us/graph/api/accessreviewset-list-definitions?view=graph-rest-1.0) | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) collection | Get a list of the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) objects and their properties. |
| [Create definitions](https://learn.microsoft.com/en-us/graph/api/accessreviewset-post-definitions?view=graph-rest-1.0) | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) | Create a new [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object. |
| [Get accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/accessreviewscheduledefinition-get?view=graph-rest-1.0) | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) | Read the properties and relationships of an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object. |
| [Update accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/accessreviewscheduledefinition-update?view=graph-rest-1.0) | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) | Update the properties of an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object. |
| [Delete accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/accessreviewscheduledefinition-delete?view=graph-rest-1.0) | None | Deletes an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object. |
| [filterByCurrentUser](https://learn.microsoft.com/en-us/graph/api/accessreviewscheduledefinition-filterbycurrentuser?view=graph-rest-1.0) | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) collection | Returns all definitions where the calling user is the reviewer of any instances. |
| **Instances** |  |  |
| [List instances](https://learn.microsoft.com/en-us/graph/api/accessreviewscheduledefinition-list-instances?view=graph-rest-1.0) | [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) collection | Get a list of the [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) objects and their properties. |
| [Get accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-get?view=graph-rest-1.0) | [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) | Read the properties and relationships of an [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) object. |
| [stop](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-stop?view=graph-rest-1.0) | None | Manually stop an accessReviewInstance. |
| [sendReminder](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-sendreminder?view=graph-rest-1.0) | None | Send a reminder to the reviewers of an accessReviewInstance. |
| [resetDecisions](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-resetdecisions?view=graph-rest-1.0) | None | Resets all decision items on an instance to `notReviewed` |
| [applyDecisions](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-applydecisions?view=graph-rest-1.0) | None | Manually apply decision on an accessReviewInstance. |
| [acceptRecommendations](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-acceptrecommendations?view=graph-rest-1.0) | None | Allows the calling user to accept the decision recommendation for each NotReviewed accessReviewInstanceDecisionItem that they are the reviewer on for a specific accessReviewInstance. |
| [batchRecordDecisions](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-batchrecorddecisions?view=graph-rest-1.0) | None | Review batches of principals or resources in one call. |
| [filterByCurrentUser](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-filterbycurrentuser?view=graph-rest-1.0) | [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) collection | Returns all instance objects on a definition for which the calling user is the reviewer. |
| **Instance decision items** |  |  |
| [List decisions](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-list-decisions?view=graph-rest-1.0) | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) collection | Get a list of the [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) objects and their properties. |
| [Get accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/accessreviewinstancedecisionitem-get?view=graph-rest-1.0) | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) | Read the properties and relationships of an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) object. |
| [Update accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/accessreviewinstancedecisionitem-update?view=graph-rest-1.0) | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) | Update the properties of an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) object. |
| [accessReviewInstanceDecisionItem: filterByCurrentUser](https://learn.microsoft.com/en-us/graph/api/accessreviewinstancedecisionitem-filterbycurrentuser?view=graph-rest-1.0) | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) collection | Returns the decision items for which the calling user is the reviewer of. |
| **History definitions** |  |  |
| [List historyDefinitions](https://learn.microsoft.com/en-us/graph/api/accessreviewset-list-historydefinitions?view=graph-rest-1.0) | [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) collection | Get a list of the [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) objects and their properties. |
| [Create historyDefinitions](https://learn.microsoft.com/en-us/graph/api/accessreviewset-post-historydefinitions?view=graph-rest-1.0) | [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) | Create a new [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) object. |
| [Get accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/accessreviewhistorydefinition-get?view=graph-rest-1.0) | [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) | Read the properties and relationships of an [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) object. |
| [generateDownloadUri](https://learn.microsoft.com/en-us/graph/api/accessreviewhistoryinstance-generatedownloaduri?view=graph-rest-1.0) | [accessReviewHistoryInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryinstance?view=graph-rest-1.0) | Generate a URI for an instance that can be used to retrieve review history data. |
| [List instances](https://learn.microsoft.com/en-us/graph/api/accessreviewhistorydefinition-list-instances?view=graph-rest-1.0) | [accessReviewHistoryInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryinstance?view=graph-rest-1.0) | Retrieve a list of the [accessReviewHistoryInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryinstance?view=graph-rest-1.0) objects and their properties. |

## Role and application permission authorization checks

The following [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) are required for a calling user to manage access reviews.

| Operation | Application permissions | Least privileged directory role of the calling user |
| :--- | :--- | :--- |
| Read | AccessReview.Read.All or AccessReview.ReadWrite.All | Global Reader, Security Administrator, Security Reader or User Administrator |
| Create, Update or Delete | AccessReview.ReadWrite.All | User Administrator |

In addition, a user who is an assigned reviewer of an access review can manage their decisions, without needing to be in a directory role.

## Related content

- [Walk through guided tutorials](https://learn.microsoft.com/en-us/graph/tutorial-accessreviews-securitygroup) to learn how to use the access reviews API to review access to Microsoft Entra resources.
