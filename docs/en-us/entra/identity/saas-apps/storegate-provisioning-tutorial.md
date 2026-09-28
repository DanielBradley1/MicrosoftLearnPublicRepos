<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/storegate-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Configure Storegate for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Storegate and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Storegate.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Storegate.
- Remove users in Storegate when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Storegate.
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- 

  - A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
  - One of the following roles:

    - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
    - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
    - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Storegate tenant](https://www.storegate.com)
- A user account on a Storegate with Administrator permissions.

## Step 1: Assign users to Storegate

Microsoft Entra ID uses a concept called assignments to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Storegate. Once decided, you can assign these users and/or groups to Storegate by following the instructions [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal).

### Important tips for assigning users to Storegate

- It's recommended that a single Microsoft Entra user is assigned to Storegate to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Storegate, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Step 2: Set up Storegate for provisioning

Before configuring Storegate for automatic user provisioning with Microsoft Entra ID, you need to retrieve some provisioning information from Storegate.

1. Sign in to your [Storegate Admin Console](https://ws1.storegate.com/identity/core/login?signin=c71fb8fe18243c571da5b333d5437367) and navigate to the settings by selecting the user icon in the upper right corner and select **Account Settings**.

   ![Screenshot of the Storegate Add SCIM integration page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/storegate-provisioning-tutorial/admin.png)

2. Within settings navigate to **Team > Settings** and verify that the toggle switch is switched on in the **Single sign-on** section.

   ![Screenshot of the Storegate team settings page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/storegate-provisioning-tutorial/team.png)


   ![Screenshot of the Storegate SSO toggle button settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/storegate-provisioning-tutorial/sso.png)

3. Copy the **Tenant URL** and **Token**. These values are entered in the **Tenant URL** and **Secret Token** fields respectively in the Provisioning tab of your Storegate application.

## Step 3: Add Storegate from the gallery

To configure Storegate for automatic user provisioning with Microsoft Entra ID, you need to add Storegate from the Microsoft Entra application gallery to your list of managed SaaS applications.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Storegate**, select **Storegate** in the results panel.

   ![Screenshot of Storegate in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

4. Select the **Sign-up for Storegate** button which will redirect you to Storegate's login page.

   ![Screenshot of the Storegate OIDC Add signup page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/storegate-provisioning-tutorial/signup.png)

5. Sign in to your [Storegate Admin Console](https://ws1.storegate.com/identity/core/login?signin=c71fb8fe18243c571da5b333d5437367) and navigate to the settings by selecting the user icon in the upper right corner and select **Account Settings**.

   ![Screenshot of the Storegate admin console login page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/storegate-provisioning-tutorial/admin.png)

6. Within settings navigate to **Team > Settings** and select toggle switch in the Single sign-on section, this will start the consent-flow. Select **Activate**.

   ![Screenshot of the Storegate team settings page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/storegate-provisioning-tutorial/team.png)


   ![Screenshot of the Storegate SSO configuration toggle.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/storegate-provisioning-tutorial/sso.png)

7. As Storegate is an OpenIDConnect app, choose to log in to Storegate using your Microsoft work account.

   ![Screenshot of the Storegate OIDC login dialog.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/storegate-provisioning-tutorial/login.png)

8. After a successful authentication, accept the consent prompt for the consent page. The application is then automatically added to your tenant and you'll be redirected to your Storegate account.

## Step 4: Configure automatic user provisioning to Storegate

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Storegate based on user and/or group assignments in Microsoft Entra ID.

Note

To learn more about Storegate's SCIM endpoint, refer [this](https://en-support.storegate.com/article/step-by-step-instruction-how-to-enable-azure-provisioning-to-your-storegate-team-account/).

### Configure automatic user provisioning for Storegate in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Storegate in the search results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

3. In the applications list, select **Storegate**.

   ![Screenshot of Storegate link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of the New configuration option on the Provisioning page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Storegate Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Storegate. If the connection fails, ensure your Storegate account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

   ![Screenshot of the Provisioning properties page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Storegate in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Storegate for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Storegate |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | active | Boolean |  |  |
    | preferredLanguage | String |  |  |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
12. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 5: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
