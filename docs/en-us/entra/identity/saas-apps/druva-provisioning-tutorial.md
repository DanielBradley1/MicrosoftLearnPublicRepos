<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/druva-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-26 -->

# Configure Druva for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Druva and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Druva.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Druva.
- Remove users in Druva when they don't require access anymore.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/druva-tutorial) to Druva \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..

- [A Druva tenant](https://www.druva.com/products/pricing-plans/).
- A user account in Druva with Admin permissions.

## Assigning users to Druva

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Druva. Once decided, you can assign these users and/or groups to Druva by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to Druva

- It's recommended that a single Microsoft Entra user is assigned to Druva to test the automatic user provisioning configuration. More users and/or groups may be assigned later.
- When assigning a user to Druva, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Set up Druva for provisioning

Before configuring Druva for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on Druva.

1. Sign in to your [Druva Admin Console](https://console.druva.com). Navigate to **Druva** > **inSync**.

   ![Screenshot of Druva Admin Console.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/druva-provisioning-tutorial/menubar.png)

2. Navigate to **Manage** > **Deployments** > **Users**.

   ![Screenshot of the Druva admin console. Manage is highlighted, and the Manage menu is visible. In that menu, under Deployments, Users are highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/druva-provisioning-tutorial/manage.png)

3. Navigate to **Settings**. Select **Generate Token**.

   ![Screenshot of a page in the Druva admin console. Settings are highlighted, and the Settings tab is open. The Generate token button is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/druva-provisioning-tutorial/settings.png)

4. Copy the **Auth token** value. This value is entered in the **Secret Token** field in the Provisioning tab of your Druva application.

   ![Screenshot of the Create token page in the Druva admin console. A link labeled Copy Token is available for copying the Auth token value.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/druva-provisioning-tutorial/auth.png)

## Add Druva from the gallery

To configure Druva for automatic user provisioning with Microsoft Entra ID, you need to add Druva from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Druva from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Druva**, select **Druva** in the search box.
4. Select **Druva** from results panel and then add the app. Wait a few seconds while the app is added to your tenant. ![Screenshot of Druva in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configuring automatic user provisioning to Druva

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Druva based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Druva, following the instructions provided in the [Druva Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/druva-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other.

### To configure automatic user provisioning for Druva in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Druva**.

   ![Screenshot of The Druva link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Druva Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Druva. If the connection fails, ensure your Druva account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.
10. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to Druva in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Druva for update operations. Select the **Save** button to commit any changes.

    ![Screenshot of Druva User Attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/druva-provisioning-tutorial/userattribute.png)

13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

    For more information on how to read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).

## Connector limitations

- Druva requires **email** as a mandatory attribute.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal).
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).
