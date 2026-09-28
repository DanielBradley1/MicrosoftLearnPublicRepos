<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-enterprise-server-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# Configure GitHub Enterprise Server for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both GitHub Enterprise Server and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and/or groups to GitHub Enterprise Server using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in GitHub Enterprise Server
- Remove users in GitHub Enterprise Server when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and GitHub Enterprise Server
- Provision groups and group memberships in GitHub Enterprise Server
- Single sign-on to [GitHub Enterprise Server](https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-enterprise-server-tutorial) \(recommended\)
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- GitHub Enterprise Server, fully [initialized](https://docs.github.com/enterprise-server/admin/overview/about-github-enterprise-server) and configured for login with [SAML SSO](https://docs.github.com/enterprise-server/admin/managing-iam/using-saml-for-enterprise-iam/configuring-saml-single-sign-on-for-your-enterprise) through your Microsoft Entra tenant.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and GitHub Enterprise Server](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure GitHub Enterprise Server to support provisioning with Microsoft Entra ID

Learn how to enable provisioning for GitHub Enterprise Server [here](https://docs.github.com/enterprise-server/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users).

## Step 3: Add GitHub Enterprise Server from the Microsoft Entra application gallery

Add GitHub Enterprise Server from the Microsoft Entra application gallery to start managing provisioning to GitHub Enterprise Server. If you have previously setup GitHub Enterprise Server for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to GitHub Enterprise Server

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for GitHub Enterprise Server in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of the Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **GitHub Enterprise Server**.

   ![Screenshot of the GitHub Enterprise Server link highlighted in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Provisioning tab selected in the application menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, input your GitHub Enterprise Server **Tenant URL** and **Secret Token**. The values of the fields are in the following format:

   - **Tenant URL**: `https://<your-github-server-domain>/api/v3/scim`
   - **Secret Token**: [The Personal Access Token \(PAT\)](https://docs.github.com/enterprise-server/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users#2-create-a-personal-access-token) you created for [the provisioning account](https://docs.github.com/enterprise-server/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users#1-create-a-built-in-setup-user) in your GitHub Enterprise Server instance.


   Select **Test Connection** to ensure Microsoft Entra ID can connect to GitHub Enterprise Server. If the connection fails, ensure your GitHub Enterprise Server account has Admin permissions and try again.


   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to GitHub Enterprise Server in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in GitHub Enterprise Server for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the GitHub Enterprise Server API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | `userName` | String |
    | `externalId` | String |
    | `emails[type eq "work"].value` | String |
    | `active` | Boolean |
    | `name.givenName` | String |
    | `name.familyName` | String |
    | n`ame.formatted` | String |
    | `displayName` | String |
12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to GitHub Enterprise Server in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in GitHub Enterprise Server for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | `displayName` | String |
    | `externalId` | String |
    | `members` | Reference |
14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Change log

- 02/18/2021 - Added support for Groups provisioning.
- 08/19/2025 - Updated links and mentions of "GitHub AE" to "GitHub Enterprise Server" to reflect the current product name.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
