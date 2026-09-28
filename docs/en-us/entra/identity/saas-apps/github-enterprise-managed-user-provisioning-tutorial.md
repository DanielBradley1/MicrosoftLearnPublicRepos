<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-enterprise-managed-user-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-26 -->

# Configure GitHub Enterprise Managed User for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both GitHub Enterprise Managed User and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and deprovisions users and groups to GitHub Enterprise Managed User using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

Note

[GitHub Enterprise Managed User \(EMU\)](https://docs.github.com/enterprise-cloud@latest/admin/authentication/managing-your-enterprise-users-with-your-identity-provider/about-enterprise-managed-users) is a different type of [GitHub Enterprise Account](https://docs.github.com/enterprise-cloud@latest/admin/overview/about-enterprise-accounts). If you haven't specifically requested EMU instance, you have a standard GitHub Enterprise Account. In that case, please refer to [the documentation](https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-provisioning-tutorial) to configure user provisioning in your non-EMU organisation. User provisioning isn't supported for [standard GitHub Enterprise Accounts](https://docs.github.com/enterprise-cloud@latest/admin/overview/about-enterprise-accounts), but is supported for organisations under GitHub Enterprise Managed User \(EMU\).

## Capabilities Supported

- Create users in GitHub Enterprise Managed User
- Remove users in GitHub Enterprise Managed User when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and GitHub Enterprise Managed User
- Provision groups and group memberships in GitHub Enterprise Managed User
- Single sign-on to GitHub Enterprise Managed User \(recommended\)
- Long lived bearer token authentication supported.

GitHub Enterprise Managed User is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- Enterprise Managed Users enabled GitHub Enterprise and configured to log in with SAML SSO through your Microsoft Entra tenant.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and GitHub Enterprise Managed User](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Prepare to configure provisioning with Microsoft Entra ID

1. Identify your Tenant URL. This is the value that you enter in the Tenant URL field in the Provisioning tab of your GitHub Enterprise Managed User application.

   - For an enterprise on GitHub.com, the Tenant URL is `https://api.github.com/scim/v2/enterprises/{enterprise}`, where `{enterprise}` is your enterprise slug \(account name\).
   - For an enterprise on GHE.com, the Tenant URL is `https://api.{subdomain}.ghe.com/scim/v2/enterprises/{subdomain}`

2. Ensure you have created a token with the **scim:enterprise** scope for your enterprise's setup user. This value is entered in the Secret Token field in the Provisioning tab of your GitHub Enterprise Managed User application. See [Getting started with Enterprise Managed Users](https://docs.github.com/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users#create-a-personal-access-token) on GitHub Docs.

## Step 3: Add GitHub Enterprise Managed User from the Microsoft Entra application gallery

Add GitHub Enterprise Managed User from the Microsoft Entra application gallery to start managing provisioning to GitHub Enterprise Managed User. If you have previously setup GitHub Enterprise Managed User for SSO, you can use the same application. However it's recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to GitHub Enterprise Managed User

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for GitHub Enterprise Managed User in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **GitHub Enterprise Managed User**.

   ![The GitHub Enterprise Managed User link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your GitHub Enterprise Managed User Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to GitHub Enterprise Managed User. If the connection fails, ensure your GitHub Enterprise Managed User account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to GitHub Enterprise Managed User in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in GitHub Enterprise Managed User for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the GitHub Enterprise Managed User API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported For Filtering |
    | --- | --- | --- |
    | externalId | String | ✓ |
    | userName | String |  |
    | active | Boolean |  |
    | roles | String |  |
    | displayName | String |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | name.formatted | String |  |
    | emails\[type eq "work"\].value | String |  |
    | emails\[type eq "home"\].value | String |  |
    | emails\[type eq "other"\].value | String |  |
12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to GitHub Enterprise Managed User in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in GitHub Enterprise Managed User for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported For Filtering |
    | --- | --- | --- |
    | externalId | String | ✓ |
    | displayName | String |  |
    | members | Reference |  |
14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
