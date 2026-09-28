<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/priority-matrix-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-09 -->

# Configure Priority Matrix for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Priority Matrix and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Priority Matrix.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

Priority Matrix is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Priority Matrix tenant](https://appfluence.com/pricing/).
- A user account on a Priority Matrix with Admin permissions.

## Assign users to Priority Matrix

Microsoft Entra ID uses a concept called assignments to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Priority Matrix. Once decided, you can assign these users and/or groups to Priority Matrix by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Priority Matrix

- It's recommended that a single Microsoft Entra user is assigned to Priority Matrix to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Priority Matrix, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Set up Priority Matrix for provisioning

Before configuring Priority Matrix for automatic user provisioning with Microsoft Entra ID, you need to retrieve some provisioning information from Priority Matrix.

1. Sign in to your [Priority Matrix Admin Console](https://sync.appfluence.com/accounts/login/?next=/accounts/provisioning).
2. Select **Oauth login token** for Priority Matrix

   ![Priority Matrix Add SCIM.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/priority-matrix-provisioning-tutorial/oauthlogin.png)

3. Select the **GET NEW TOKEN** button. Copy the **Token String**. This value is entered in the **Secret Token** field in the Provisioning tab of your Priority Matrix application.

## Add Priority Matrix from the gallery

To configure Priority Matrix for automatic user provisioning with Microsoft Entra ID, you need to add Priority Matrix from the Microsoft Entra application gallery to your list of managed SaaS applications.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Priority Matrix**, select **Priority Matrix** in the results panel.

   ![Priority Matrix in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

4. Select the **Sign-up for Priority Matrix** button which will redirect you to Priority Matrix's login page.

   ![Priority Matrix OIDC Add](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/priority-matrix-provisioning-tutorial/signup.png)

5. As Priority Matrix is an OpenIDConnect app, choose to sign in to Priority Matrix using your Microsoft work account.

   ![Priority Matrix OIDC login](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/priority-matrix-provisioning-tutorial/msftsignin.png)

6. After a successful authentication, accept the consent prompt for the consent page. The application will then be automatically added to your tenant and you'll be redirected to your Priority Matrix account.

## Configure automatic user provisioning to Priority Matrix

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Priority Matrix based on user and/or group assignments in Microsoft Entra ID.

Note

To learn more about Priority Matrix's SCIM endpoint, refer to [User provisioning and Priority Matrix](https://appfluence.com/help/article/user-provisioning/).

### To configure automatic user provisioning for Priority Matrix in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Priority Matrix**.

   ![The Priority Matrix link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Priority Matrix Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Priority Matrix. If the connection fails, ensure your Priority Matrix account has the required admin permissions and try again.

   Note

   Enter `https://sync.appfluence.com/scim/v2/` in the **Tenant URL**.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of the Provisioning properties page showing notification and deletion settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Priority Matrix in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Priority Matrix for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Priority Matrix API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

    ![Screenshot of the Priority Matrix User Attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/priority-matrix-provisioning-tutorial/userattributes.png)

12. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
