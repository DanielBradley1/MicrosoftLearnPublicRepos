<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-21 -->

# Microsoft Entra access reviews \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

You can use [Microsoft Entra access reviews](https://learn.microsoft.com/en-us/azure/active-directory/active-directory-azure-ad-controls-access-reviews-overview) to configure one-time or recurring access reviews for attestation of user's access rights.

Typical customer scenarios for access reviews of group memberships and application access are:

- Customers can review and certify guest user access by using access reviews of their access to applications and memberships of groups. Reviewers can use the insights that are provided to efficiently decide whether guests should have continued access.
- Customers can review and certify employee access to applications and group memberships with access reviews.
- Customers can collect access review controls into programs that are relevant for your organization to track reviews for compliance or risk-sensitive applications.

There's also a related capability for customers to review and certify the role assignments of administrative users who are assigned to [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or [Azure subscription](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) roles. This capability is included in [Microsoft Entra Privileged Identity Management](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-beta).

The tenant where an access review is being created or managed via the API must have sufficient purchased or trial licenses. For more information about the license requirements, see [Access reviews license requirements](https://learn.microsoft.com/en-us/azure/active-directory/governance/access-reviews-overview#license-requirements).

Prior to creating an access review, program or program control, an administrator must have previously onboarded in order to prepare the [programControlType](https://learn.microsoft.com/en-us/graph/api/resources/programcontroltype?view=graph-rest-beta) and [businessFlowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/businessflowtemplate?view=graph-rest-beta) resources. The organization can onboard to Microsoft Entra access reviews or, in the case of access reviews of Microsoft Entra roles or Azure subscription roles, Microsoft Entra PIM.

## Methods

The following table lists the methods that you can use to interact with access review-related resources.

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get accessReview](https://learn.microsoft.com/en-us/graph/api/accessreview-get?view=graph-rest-beta) | [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) | Get an access review with a specific ID. |
| [Create accessReview](https://learn.microsoft.com/en-us/graph/api/accessreview-create?view=graph-rest-beta) | [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) | Create a new accessReview. |
| [Delete accessReview](https://learn.microsoft.com/en-us/graph/api/accessreview-delete?view=graph-rest-beta) | None. | Delete an accessReview. |
| [Update accessReview](https://learn.microsoft.com/en-us/graph/api/accessreview-update?view=graph-rest-beta) | [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) | Update an accessReview. |
| [List accessReviews](https://learn.microsoft.com/en-us/graph/api/accessreview-list?view=graph-rest-beta) | [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) collection | List accessReviews for a businessFlowTemplate. |
| [List accessReview reviewers](https://learn.microsoft.com/en-us/graph/api/accessreview-listreviewers?view=graph-rest-beta) | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta) collection | Get the reviewers of an accessReview. |
| [Add accessReview reviewer](https://learn.microsoft.com/en-us/graph/api/accessreview-addreviewer?view=graph-rest-beta) | None. | Add a reviewer to an accessReview. |
| [Remove accessReview reviewer](https://learn.microsoft.com/en-us/graph/api/accessreview-removereviewer?view=graph-rest-beta) | None. | Remove a reviewer from an accessReview. |
| [List accessReview decisions](https://learn.microsoft.com/en-us/graph/api/accessreview-listdecisions?view=graph-rest-beta) | [accessReviewDecision](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewdecision?view=graph-rest-beta) collection | Get the decisions of an accessReview. |
| [List my accessReview decisions](https://learn.microsoft.com/en-us/graph/api/accessreview-listmydecisions?view=graph-rest-beta) | [accessReviewDecision](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewdecision?view=graph-rest-beta) collection | As a reviewer, get my decisions of an accessReview. |
| [Send accessReview reminder](https://learn.microsoft.com/en-us/graph/api/accessreview-sendreminder?view=graph-rest-beta) | None. | Send a reminder to the reviewers of an accessReview. |
| [Stop accessReview](https://learn.microsoft.com/en-us/graph/api/accessreview-stop?view=graph-rest-beta) | None. | Stop an accessReview. |
| [Reset accessReview decisions](https://learn.microsoft.com/en-us/graph/api/accessreview-reset?view=graph-rest-beta) | None. | Reset the decisions in an in-progress accessReview. |
| [Apply accessReview decisions](https://learn.microsoft.com/en-us/graph/api/accessreview-apply?view=graph-rest-beta) | None. | Apply the decisions from a completed accessReview. |
| [List businessFlowTemplates](https://learn.microsoft.com/en-us/graph/api/businessflowtemplate-list?view=graph-rest-beta) | [businessFlowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/businessflowtemplate?view=graph-rest-beta) collection | Get the business flow templates appropriate to access reviews. |
| [Create program](https://learn.microsoft.com/en-us/graph/api/program-create?view=graph-rest-beta) | [program](https://learn.microsoft.com/en-us/graph/api/resources/program?view=graph-rest-beta) | Create a new program. |
| [Delete program](https://learn.microsoft.com/en-us/graph/api/program-delete?view=graph-rest-beta) | None. | Delete a program. |
| [List programs](https://learn.microsoft.com/en-us/graph/api/program-list?view=graph-rest-beta) | [program](https://learn.microsoft.com/en-us/graph/api/resources/program?view=graph-rest-beta) collection | Get a collection of all the programs. |
| [List programControls of a program](https://learn.microsoft.com/en-us/graph/api/program-listcontrols?view=graph-rest-beta) | [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) collection | Get a collection of the controls of a program. |
| [Update program](https://learn.microsoft.com/en-us/graph/api/program-update?view=graph-rest-beta) | [program](https://learn.microsoft.com/en-us/graph/api/resources/program?view=graph-rest-beta) | Update a program. |
| [Create programControl](https://learn.microsoft.com/en-us/graph/api/programcontrol-create?view=graph-rest-beta) | [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) | Add a programControl to a program. |
| [Delete programControl](https://learn.microsoft.com/en-us/graph/api/programcontrol-delete?view=graph-rest-beta) | None. | Remove a programControl from a program. |
| [List programControls](https://learn.microsoft.com/en-us/graph/api/programcontrol-list?view=graph-rest-beta) | [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) collection | List controls across all programs in the tenant. |
| [List programControlTypes](https://learn.microsoft.com/en-us/graph/api/programcontroltype-list?view=graph-rest-beta) | [programControlType](https://learn.microsoft.com/en-us/graph/api/resources/programcontroltype?view=graph-rest-beta) collection | List program control types. |

## Role and application permission authorization checks

The following directory roles are required for a calling user to manage access reviews, programs, and controls.

| Target resource | Operation | Application permissions | Least privileged directory roles of the calling user |
| :--- | :--- | :--- | :--- |
| [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) of a Microsoft Entra role | Read | AccessReview.Read.All or AccessReview.ReadWrite.All | Global Reader, Security Administrator, Security Reader or Privileged Role Administrator |
| [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) of a Microsoft Entra role | Create, Update, or Delete | AccessReview.ReadWrite.All | Privileged Role Administrator |
| [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) of a group or app | Read | AccessReview.Read.All, AccessReview.ReadWrite.Membership, or AccessReview.ReadWrite.All | Global Reader, Security Administrator, Security Reader, or User Administrator |
| [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) of a group or app | Create, Update, or Delete | AccessReview.ReadWrite.Membership or AccessReview.ReadWrite.All | User Administrator |
| [program](https://learn.microsoft.com/en-us/graph/api/resources/program?view=graph-rest-beta) and [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) | Read | ProgramControl.Read.All or ProgramControl.ReadWrite.All | Global Reader, Security Administrator, Security Reader or User Administrator |
| [program](https://learn.microsoft.com/en-us/graph/api/resources/program?view=graph-rest-beta) and [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) | Create, Update, or Delete | ProgramControl.ReadWrite.All | User Administrator |

In addition, a user who is an assigned reviewer of an access review can manage their decisions, without needing to be in a directory role.

## Related content

- [How an administrator can manage user access with Microsoft Entra access reviews](https://learn.microsoft.com/en-us/azure/active-directory/active-directory-azure-ad-controls-manage-user-access-with-access-reviews)
- [How an administrator can manage guest access with Microsoft Entra access reviews](https://learn.microsoft.com/en-us/azure/active-directory/active-directory-azure-ad-controls-manage-guest-access-with-access-reviews)
- [How an administrator can manage programs and controls for Microsoft Entra access reviews](https://learn.microsoft.com/en-us/azure/active-directory/active-directory-azure-ad-controls-manage-programs-controls)
