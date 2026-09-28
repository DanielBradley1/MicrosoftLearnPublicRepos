<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/workteam-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-26 -->

# Configure Workteam for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Workteam and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Workteam.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Workteam.
- Remove users in Workteam when they don't require access anymore.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/workteam-tutorial) to Workteam \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- \- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..
- [A Workteam tenant](https://workte.am/pricing.html)
- A user account in Workteam with Admin permissions.

## Step 1: Assign users to Workteam

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Workteam. Once decided, you can assign these users and/or groups to Workteam by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Workteam

- It's recommended that a single Microsoft Entra user is assigned to Workteam to test the automatic user provisioning configuration. More users and/or groups may be assigned later.
- When assigning a user to Workteam, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Step 2: Set up Workteam for provisioning

Before configuring Workteam for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on Workteam.

1. Log in into [Workteam](https://app.workte.am/account/signin). Select **Organization settings** > **SETTINGS**.

   ![Screenshot of the Workteam U I with the Organization settings and SETTINGS options called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/workteam-provisioning-tutorial/settings.png)

2. Scroll to bottom and enable the provisioning capabilities of Workteam.

   ![Screenshot of the bottom of the SETTINGS section with the S C I M User Provisioning gear icon called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/workteam-provisioning-tutorial/icon.png)

3. Copy the **Base Url** and **Bearer Token**. These values are entered in the **Tenant URL** and **Secret Token** field in the Provisioning tab of your Workteam application.

   ![Screenshot of the S C I M Settings dialog box with the BASE U R L and BEARER TOKEN text boxes called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/workteam-provisioning-tutorial/scim.png)

## Step 3: Add Workteam from the gallery

To configure Workteam for automatic user provisioning with Microsoft Entra ID, you need to add Workteam from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Workteam from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Workteam**, select **Workteam** in the search box.
4. Select **Workteam** from results panel and then add the app. Wait a few seconds while the app is added to your tenant. ![Workteam in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Step 4: Configure automatic user provisioning to Workteam

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Workteam based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Workteam, following the instructions provided in the [Workteam Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/workteam-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other

### Configure automatic user provisioning for Workteam in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Workteam**.

   ![Screenshot of the Workteam link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of new configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Workteam Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Workteam. If the connection fails, ensure your Workteam account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Workteam in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Workteam for update operations. Select the **Save** button to commit any changes.

    ![Screenshot of Workteam User Attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/workteam-provisioning-tutorial/userattribute.png)

12. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 5: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
