<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/elium-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Configure Elium for automatic user provisioning with Microsoft Entra ID

This article shows how to configure Elium and Microsoft Entra ID to automatically provision and de-provision users or groups to Elium.

Note

This article describes a connector that's built on top of the Microsoft Entra user provisioning service. For important details about what this service does and how it works, and for frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

This connector is currently in preview. For more information about previews, see [Universal License Terms For Online Services](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all).

Elium is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Capabilities supported

- Create users in Elium.
- Remove users in Elium when they don't require access anymore.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/elium-tutorial) to Elium \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

This article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [An Elium tenant](https://www.elium.com/pricing/)
- A user account in Elium, with admin permissions

## Assigning users to Elium

Microsoft Entra ID uses a concept called *assignments* to determine which users receive access to selected apps. In the context of automatic user provisioning, only the users and groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before you configure and enable automatic user provisioning, decide which users and groups in Microsoft Entra ID need access to Elium. Then, assign those users and groups to Elium by following the steps in [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal).

## Important tips for assigning users to Elium

We recommend that you assign a single Microsoft Entra user to Elium to test the automatic user-provisioning configuration. More users and groups can be assigned later.

When assigning a user to Elium, you must select a valid, application-specific role \(if any are available\) in the assignment dialog box. Users who have the **Default Access** role are excluded from provisioning.

## Set up Elium for provisioning

Before configuring Elium for automatic user provisioning with Microsoft Entra ID, you must enable System for Cross-domain Identity Management \(SCIM\) provisioning on Elium. Follow these steps:

1. Sign in to Elium and go to **My Profile** > **Settings**.

   ![Settings menu item in Elium](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/elium-provisioning-tutorial/setting.png)

2. In the lower-left corner, under **ADVANCED**, select **Security**.

   ![Security link in Elium](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/elium-provisioning-tutorial/security.png)

3. Copy the **Tenant URL** and **Secret token** values. You'll use these values later, in corresponding fields in the **Provisioning** tab of your Elium application.

   ![Tenant URL and Secret token fields in Elium](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/elium-provisioning-tutorial/token.png)

## Add Elium from the gallery

To configure Elium for automatic user provisioning with Microsoft Entra ID, you must also add Elium from the Microsoft Entra application gallery to your list of managed software-as-a-service \(SaaS\) applications. Follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.

   ![Microsoft Entra Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. To add a new application, select **New application** at the top of the pane.

   ![New application link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/add-new-app.png)

4. In the search box, type **Elium**, select **Elium** in the results list, and then select **Add** to add the application.

   ![Gallery search box](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configure automatic user provisioning to Elium

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and groups in Elium, based on user and group assignments in Microsoft Entra ID.

Tip

You might also choose to enable single sign-on for Elium based on Security Assertion Markup Language \(SAML\) by following the instructions in the [Elium single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/elium-tutorial). You can configure single sign-on independently of automatic user provisioning, although the two features complement each other.

To configure automatic user provisioning for Elium in Microsoft Entra ID, follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Microsoft Entra Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Elium**.

   ![Applications list in the Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab in the Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Elium Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Elium. If the connection fails, ensure your Elium account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Elium in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Elium for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Elium API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

    ![Attribute mappings between Microsoft Entra ID and Elium](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/elium-provisioning-tutorial/userattribute.png)

12. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal).
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
