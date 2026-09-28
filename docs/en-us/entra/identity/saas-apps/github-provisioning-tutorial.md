<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-13 -->

# Configure GitHub for automatic user provisioning in Microsoft Entra ID

The objective of this article is to show you the steps you need to perform in GitHub and Microsoft Entra ID to automate provisioning of GitHub Enterprise Cloud organization membership.

Note

The Microsoft Entra provisioning integration relies on the [GitHub SCIM API](https://developer.github.com/v3/scim/), which is available to [GitHub Enterprise Cloud](https://help.github.com/articles/github-s-products/#github-enterprise) customers on the [GitHub Enterprise billing plan](https://help.github.com/articles/github-s-billing-plans/#billing-plans-for-organizations).

Github is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following items:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A GitHub organization created in [GitHub Enterprise Cloud](https://help.github.com/articles/github-s-products/#github-enterprise), which requires the [GitHub Enterprise billing plan](https://help.github.com/articles/github-s-billing-plans/#billing-plans-for-organizations)
- A user account in GitHub with Admin permissions to the organization
- [SAML configured for the GitHub Enterprise Cloud organization](https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-tutorial)
- Ensure that OAuth access has been provided for your organization as described [here](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/approving-oauth-apps-for-your-organization)
- SCIM provisioning to a single organization is supported only when SSO is enabled at the organization level

## Assigning users to GitHub

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Microsoft Entra ID is synchronized.

Before configuring and enabling the provisioning service, you need to decide what users and/or groups in Microsoft Entra ID represent the users who need access to your GitHub Organization. Once decided, you can assign these users by following the instructions here:

For more information, see [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal).

### Important tips for assigning users to GitHub

- We recommend that you assign a single Microsoft Entra user to GitHub to test the provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to GitHub, you must select either the **User** role, or another valid application-specific role \(if available\) in the assignment dialog. The **Default Access** role doesn't work for provisioning, and these users are skipped.

## Configuring user provisioning to GitHub

This section guides you through connecting your Microsoft Entra ID to GitHub's SCIM provisioning API to automate provisioning of GitHub organization membership. This integration, which leverages an [OAuth app](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/authorizing-oauth-apps#oauth-apps-and-organizations), automatically adds, manages, and removes members' access to a GitHub Enterprise Cloud organization based on user and group assignment in Microsoft Entra ID. When users are [provisioned to a GitHub organization via SCIM](https://docs.github.com/en/rest/enterprise-admin/scim), an email invitation is sent to the user's email address.

### Configure automatic user account provisioning to GitHub in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.
3. If you have already configured GitHub for single sign-on, search for your instance of GitHub using the search field.
4. Select your instance of GitHub, then select the **Provisioning** tab.
5. Select **+ New configuration**.

   ![Screenshot of the Provisioning Mode dropdown list with the Automatic option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your GitHub Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to GitHub. If the connection fails, ensure your GitHub account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. In the new window, sign into GitHub using your Admin account. In the resulting authorization dialog, select the GitHub Organization that you want to enable provisioning for, and then select **Authorize**. Once completed, return to the Azure portal to complete the provisioning configuration.

   ![Screenshot shows the sign-in page for GitHub.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/github-provisioning-tutorial/github2.png)

8. Select **Create** to create your configuration.
9. Select **Properties** on the **Overview** page.
10. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.
11. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

12. Select **Attribute Mapping** in the left panel and select **users**.
13. In the **Attribute Mappings** section, review the user attributes that are synchronized from Microsoft Entra ID to GitHub. The attributes selected as **Matching** properties are used to match the user accounts in GitHub for update operations. Don't enable the **Matching precedence** setting for the other default attributes in the **Provisioning** section because errors might occur. Select **Save** to commit any changes.
14. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

For more information on how to read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
