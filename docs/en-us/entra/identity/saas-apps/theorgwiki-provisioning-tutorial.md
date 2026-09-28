<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/theorgwiki-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Configure TheOrgWiki for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in TheOrgWiki and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to TheOrgWiki.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in TheOrgWiki.
- Remove users in TheOrgWiki when they don't require access anymore.
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- \- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..
- [An OrgWiki tenant](https://www.theorgwiki.com/welcome/).
- A user account in TheOrgWiki with Admin permissions.

## Step 1: Assign users to TheOrgWiki

Microsoft Entra ID uses a concept called assignments to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to TheOrgWiki. Once decided, you can assign these users and/or groups to TheOrgWiki by following the instructions [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal).

### Important tips for assigning users to TheOrgWiki

- It's recommended that a single Microsoft Entra user is assigned to TheOrgWiki to test the automatic user provisioning configuration. More users and/or groups may be assigned later.
- When assigning a user to TheOrgWiki, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Step 2: Set up TheOrgWiki for provisioning

Before configuring TheOrgWiki for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on TheOrgWiki.

1. Sign in to your [TheOrgWiki Admin Console](https://www.theorgwiki.com/login/). Select **Admin Console**.

   ![Screenshot of Org Wiki with the user avatar and the Admin Console called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/theorgwiki-provisioning-tutorial/login.png)

2. In Admin Console, Select **Settings tab**.

   ![Screenshot of the The Org Wiki Admin Console with the Settings tab called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/theorgwiki-provisioning-tutorial/settings.png)

3. Navigate to **Service Accounts**.

   ![Screenshot of the Service Accounts page in the Org Wiki Admin Console.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/theorgwiki-provisioning-tutorial/serviceaccount.png)

4. Select **+Service Account**. Under **Service Account Type**, select **Token Based**. Select **Save**.

   ![Screenshot of the New Service Account dialog box with the Service Account Type, Token Based, and Save options called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/theorgwiki-provisioning-tutorial/auth.png)

5. Copy the **Active Tokens**. This value is entered in the Secret Token field in the Provisioning tab of your TheOrgWiki application.

   ![Screenshot of the Manage Tokens for S C I M provisioning dialog box.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/theorgwiki-provisioning-tutorial/token.png)

## Step 3: Add TheOrgWiki from the gallery

To configure TheOrgWiki for automatic user provisioning with Microsoft Entra ID, you need to add TheOrgWiki from the Microsoft Entra application gallery to your list of managed SaaS applications.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **TheOrgWiki**, select **TheOrgWiki** in the results panel.

   ![Screenshot of TheOrgWiki in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

4. Select the **Sign-up for TheOrgWiki** button which will redirect you to TheOrgWiki's login page.

   ![Screenshot of The Org Wiki login page with the URL called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/theorgwiki-provisioning-tutorial/image00.png)

5. In the top right-hand corner, select **Login**.

   ![Screenshot of the upper-right corner of the login page with the Log In option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/theorgwiki-provisioning-tutorial/image02.png)

6. As TheOrgWiki is an OpenIDConnect app, choose to log in to OrgWiki using your Microsoft work account.

   ![Screenshot of the The Org Wiki sign in page with the Sign in with Microsoft option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/theorgwiki-provisioning-tutorial/image03.png)

7. After a successful authentication, the application is automatically added to your tenant and you'll be redirected to your TheOrgWiki account.

   ![Screenshot of OrgWiki Add SCIM.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/theorgwiki-provisioning-tutorial/image04.png)

## Step 4: Configure automatic user provisioning to TheOrgWiki

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TheOrgWiki based on user and/or group assignments in Microsoft Entra ID.

### Configure automatic user provisioning for TheOrgWiki in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **TheOrgWiki**.

   ![Screenshot of OrgWiki link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of New configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, enter `https://<TheOrgWiki Subdomain 		value>.theorgwiki.com/api/v2/scim/v2/` in **Tenant URL**.

   Example: `https://test1.theorgwiki.com/api/v2/scim/v2/`

   Note

   The **Subdomain Value** can only be set during the initial sign-up process for TheOrgWiki.
7. Enter the token value in **Secret Token** field, that you retrieved earlier from TheOrgWiki. Select **Test Connection** to ensure Microsoft Entra ID can connect to TheOrgWiki. If the connection fails, ensure your TheOrgWiki account has Admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

8. Select **Create** to create your configuration.
9. Select **Properties** on the **Overview** page.
10. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to TheOrgWiki in the **Attribute- Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in TheOrgWiki for update operations. Select the **Save** button to commit any changes.

    ![Screenshot of TheOrgWiki User Attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/theorgwiki-provisioning-tutorial/userattribute.png).
13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 5: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal).
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).
