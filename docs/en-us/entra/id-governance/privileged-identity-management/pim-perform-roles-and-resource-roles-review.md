<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-perform-roles-and-resource-roles-review -->
<!-- Sitemap-Last-Modified: 2026-04-23 -->

# Perform an access review of Azure resource and Microsoft Entra roles in PIM

## Overview

Privileged Identity Management \(PIM\) simplifies how enterprises manage privileged access to resources in Microsoft Entra ID, and other Microsoft online services like Microsoft 365 or Microsoft Intune. Follow the steps in this article to perform reviews of access to roles.

If you're assigned to an administrative role, your organization's Privileged Role Administrator may ask you to regularly confirm that you still need that role for your job. You might get an email that includes a link, or you can go straight to the [Microsoft Entra admin center](https://entra.microsoft.com) and begin.

If you're at least a Privileged Role Administrator interested in access reviews, get more details at [How to start an access review](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-create-roles-and-resource-roles-review).

## Approve or deny access

You can approve or deny access based on whether the user still needs access to the role. Choose **Approve** if you want them to stay in the role, or **Deny** if they don't need the access anymore. The users' assignment status doesn't change until the review closes and the administrator applies the results. Common scenarios in which certain denied users can't have results applied to them might include the following:

- **Reviewing members of a synced on-premises Windows AD group**: If the group is synced from an on-premises Windows AD, the group can't be managed in Microsoft Entra ID, and therefore membership can't be changed.
- **Reviewing a role with nested groups assigned**: For users who have membership through a nested group, the access review doesn't remove their membership to the nested group and therefore they retain access to the role being reviewed.
- **User not found or other errors**: These might also result in an apply result not being supported.

Follow these steps to find and complete the access review:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **ID Governance** > **Privileged Identity Management** > **Review access**.
3. If you have any pending access reviews, they appear in the access reviews page.

   [![Screenshot of Privileged Identity Management application, with Review access pane selected for Microsoft Entra roles.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-perform-azure-ad-roles-and-resource-roles-review/rbac-access-review-azure-ad-complete.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-perform-azure-ad-roles-and-resource-roles-review/rbac-access-review-azure-ad-complete.png#lightbox)
4. Select the review you want to complete.
5. Choose **Approve** or **Deny**. In the **Provide a reason box**, enter a business justification for your decision as needed.

   [![Screenshot of Privileged Identity Management application, with the selected Access Review for Microsoft Entra roles.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-perform-azure-ad-roles-and-resource-roles-review/rbac-access-review-azure-ad-completed.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-perform-azure-ad-roles-and-resource-roles-review/rbac-access-review-azure-ad-completed.png#lightbox)

## Next steps

- [Create an access review of Azure resource and Microsoft Entra roles in PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-create-roles-and-resource-roles-review)
- [Complete an access review of Azure resource and Microsoft Entra roles in PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-complete-roles-and-resource-roles-review)
