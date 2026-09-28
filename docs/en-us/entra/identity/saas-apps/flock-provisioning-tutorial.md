<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/flock-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-26 -->

# Configure Flock for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Flock and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Flock.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Flock.
- Remove users in Flock when they don't require access anymore.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/flock-tutorial) to Flock \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..

- [A Flock tenant](https://flock.com/pricing/)
- A user account in Flock with Admin permissions.

## Assigning users to Flock

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Flock. Once decided, you can assign these users and/or groups to Flock by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to Flock

- It's recommended that a single Microsoft Entra user is assigned to Flock to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Flock, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Set up Flock for provisioning

Before configuring Flock for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on Flock.

1. Log in into [Flock](https://web.flock.com/?). Select **Settings Icon** > **Manage your team**.

   ![Screenshot of the Flock website. The settings icon is highlighted and its shortcut menu is visible. In that menu, Manage your team is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/flock-provisioning-tutorial/icon.png)

2. Select **Auth and Provisioning**.

   ![Screenshot of a menu on the Flock website. The Auth and provisioning item is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/flock-provisioning-tutorial/auth.png)

3. Copy the **API Token**. These values are entered in the **Secret Token** field in the Provisioning tab of your Flock application.

   ![Screenshot of a Provisioning tab on the Flock website. Under A P I token, a value is highlighted. Next to the token is a Copy token button.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/flock-provisioning-tutorial/provisioning.png)

## Add Flock from the gallery

To configure Flock for automatic user provisioning with Microsoft Entra ID, you need to add Flock from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Flock from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Flock**, select **Flock** in the search box.
4. Select **Flock** from results panel and then add the app. Wait a few seconds while the app is added to your tenant. ![Screenshot of Flock in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configuring automatic user provisioning to Flock

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Flock based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Flock, following the instructions provided in the [Flock Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/flock-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other

### To configure automatic user provisioning for Flock in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Flock**.

   ![Screenshot of the Flock link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of the Provisioning Mode dropdown list with the Automatic option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Flock Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Flock. If the connection fails, ensure your Flock account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.
10. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to Flock in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Flock for update operations. Select the **Save** button to commit any changes.

    ![Screenshot of Flock User Attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/flock-provisioning-tutorial/userattribute.png)

13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

You can use the **Current Status** section to monitor progress and follow links to your provisioning activity report, which describes all actions performed by the Microsoft Entra provisioning service on Flock. For more information, see [Check the status of user provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user). To read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
