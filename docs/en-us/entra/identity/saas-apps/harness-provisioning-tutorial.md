<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/harness-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# Configure Harness for automatic user provisioning with Microsoft Entra ID

This article explains how to configure Microsoft Entra ID to automatically provision and deprovision users or groups to Harness. Automatic provisioning eliminates manual user management by synchronizing user lifecycle changes from your identity provider to Harness.

Note

This article describes a connector that is built on top of the Microsoft Entra user provisioning service. For information about this service, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Harness tenant](https://harness.io/pricing/)
- A user account in Harness with *Admin* permissions

## Assign users to Harness

Before you configure provisioning, you must assign users or groups to the Harness application in Microsoft Entra ID. Microsoft Entra ID uses **assignments** to determine which users should receive access to selected applications. In the context of automatic user provisioning, only the users or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before you configure and enable automatic user provisioning, decide which users or groups in Microsoft Entra ID need access to Harness. You can then assign these users or groups to Harness by following the instructions in [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal).

### Recommendations for user assignment

Start with a small test group before you roll out provisioning to your entire organization. Assign a single Microsoft Entra user to Harness to test the automatic user provisioning configuration. After you verify that provisioning works correctly, you can assign additional users or groups.

When you assign a user to Harness, you must select a valid application-specific role \(if available\) in the **Assignment** dialog box. Users with the *Default Access* role are excluded from provisioning.

If you currently have a Harness App Integration setup in Microsoft Entra ID and are now trying to set up one for Harness, ensure that the user information is also included in the App Integration before you attempt to log into Harness through SSO.

## Set up Harness for provisioning

You must generate a SCIM API token in Harness before you can configure provisioning in Microsoft Entra ID. This token allows Microsoft Entra ID to securely connect to the Harness SCIM endpoint and provision users.

1. Sign in to your [Harness Admin Console](https://app.harness.io/auth/#/signin), select your profile at the bottom left corner of the page, and go to **Profile Overview**.

   ![Screenshot of the Harness Admin Console with the profile menu used to open Profile Overview.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/harness-provisioning-tutorial/admin.png)

2. Under **My API Keys**, select **+API Key**. The window to create an API key opens.

   ![Screenshot of the Harness Profile Overview page showing the +API Key button under My API Keys.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/harness-provisioning-tutorial/apikeys.png)

3. Specify a **Name** and select **Save**. Harness creates an API key for your account.

   ![Screenshot of the Harness new API key dialog with the Name box and Save button.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/harness-provisioning-tutorial/addkey.png)

4. To create a token for your API key, select **+Token** under your newly created API key.

   a. Provide a name and select **Generate token**.

   b. Copy the token value to a safe location. You'll need this token to configure the connection in Microsoft Entra ID.

   c. Select **Close**.

   ![Screenshot of the Harness token dialog showing the Generate token and Close buttons.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/harness-provisioning-tutorial/api-token.png)

## Add Harness from the gallery

You must add the Harness application from the Microsoft Entra application gallery before you can configure automatic user provisioning. This registers Harness as a managed SaaS application in your Microsoft Entra tenant.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.

   ![The "All applications" link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. To add a new application, select the **New application** button at the top of the pane.

   ![The "New application" button](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/add-new-app.png)

4. In the search box, enter **Harness**, select **Harness** in the results list, and then select the **Add** button to add the application.

   ![Screenshot of the Microsoft Entra gallery search results with Harness selected and the Add button.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/harness-provisioning-tutorial/search-new-app.png)

## Configure automatic user provisioning to Harness

After you add Harness from the gallery and generate a SCIM token, you can configure the provisioning connection. This section walks through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users or groups in Harness based on user or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Harness by following the instructions in the [Harness single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/harness-tutorial). You can configure single sign-on independent of automatic user provisioning, although these two features complement each other.

Note

To learn more about the Harness SCIM endpoint, see the Harness [API Keys](https://developer.harness.io/docs/platform/automation/api/add-and-manage-api-keys/) article.

To configure automatic user provisioning for Harness in Microsoft Entra ID, do the following:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Harness**.

   ![The Harness link in the applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under **Admin Credentials**, do the following:

   ![Tenant URL + Token](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-testconnection-tenanturltoken.png)


   - In the **Tenant URL** box, enter **`https://app.harness.io/gateway/api/scim/account/<your_harness_account_ID>`**. You can obtain your Harness account ID from the URL in your browser when you are logged into Harness.
   - In the **Secret Token** box, enter the SCIM Authentication Token value that you saved in step 3 of the "Set up Harness for provisioning" section.
   - Select **Test Connection** to ensure that Microsoft Entra ID can connect to Harness. If the connection fails, ensure that your Harness account has *Admin* permissions, and then try again.

     ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Harness in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Harness for update operations. Select the **Save** button to commit any changes.

    ![Harness user "Attribute Mappings" pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/harness-provisioning-tutorial/userattributes.png)

12. Under **Mappings**, select **Synchronize Microsoft Entra groups to Harness**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to Harness in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Harness for update operations. Select the **Save** button to commit any changes.

    ![Harness group "Attribute Mappings" pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/harness-provisioning-tutorial/groupattributes.png)

14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you are ready to provision, select **Start Provisioning** from the **Overview** page.

## Monitor your deployment

After you start provisioning, monitor the provisioning logs to verify that users and groups sync correctly between Microsoft Entra ID and Harness.

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
- [Manage user account provisioning for enterprise apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [Application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
