<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/promapp-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-04 -->

# Configure Promapp for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Promapp and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Promapp.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Promapp tenant](https://www.promapp.com/licensing/).
- A user account in Promapp with Admin permissions.

## Assigning users to Promapp

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Promapp. Once decided, you can assign these users and/or groups to Promapp by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to Promapp

- It's recommended that a single Microsoft Entra user is assigned to Promapp to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Promapp, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Set up Promapp for provisioning

1. Sign in to your Promapp Admin Console. Under the user name navigate to **My Profile**.

   ![Promapp Admin Console](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/promapp-provisioning-tutorial/admin.png)

2. Under **Access Tokens** select the **Create Token** button.

   ![Promapp Add SCIM](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/promapp-provisioning-tutorial/addtoken.png)

3. Provide any name in the **Description** field and select **SCIM** from the **Scope** dropdown menu. Select the save icon.

   ![Promapp Add Name](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/promapp-provisioning-tutorial/addname.png)

4. Copy the access token and save it as it's the only time you can view it. This value is entered in the Secret Token field in the Provisioning tab of your Promapp application.

   ![Promapp Create Token](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/promapp-provisioning-tutorial/token.png)

## Add Promapp from the gallery

Before configuring Promapp for automatic user provisioning with Microsoft Entra ID, you need to add Promapp from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Promapp from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Promapp**, select **Promapp** in the search box.
4. Select **Promapp** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

   ![Promapp in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configuring automatic user provisioning to Promapp

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Promapp based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Promapp by following the instructions provided in the [Promapp Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/promapp-tutorial). Single sign-on can be configured independently of automatic user provisioning, although these two features complement each other.

### To configure automatic user provisioning for Promapp in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Promapp**.

   ![The Promapp link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Promapp Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Promapp. If the connection fails, ensure your Promapp account has the required admin permissions and try again.

   Note

   Enter `https://api.promapp.com/api/scim` in the **Tenant URL**.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of the Provisioning properties page showing notification and deletion settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Promapp in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Promapp for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Promapp API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

    ![Screenshot of the Promapp User Attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/promapp-provisioning-tutorial/userattributes.png)

12. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
