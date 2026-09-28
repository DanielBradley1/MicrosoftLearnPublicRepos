<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/pingboard-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Configure Pingboard for automatic user provisioning in Microsoft Entra ID

The purpose of this article is to show you the steps you need to follow to enable automatic provisioning and de-provisioning of user accounts from Microsoft Entra ID to Pingboard.

## Prerequisites

The scenario outlined in this article assumes that you already have the following items:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A Pingboard tenant [Pro account](https://pingboard.com/pricing)
- A user account in Pingboard with admin permissions

Note

Microsoft Entra provisioning integration relies on the [Pingboard API](https://pingboard.docs.apiary.io/#), which is available to your account.

## Assign users to Pingboard

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected applications. In the context of automatic user account provisioning, only the users assigned to an application in Microsoft Entra ID are synchronized.

Before you configure and enable the provisioning service, you must decide which users in Microsoft Entra ID need access to your Pingboard app. Then you can assign these users to your Pingboard app by following the instructions here:

[Assign a user to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Pingboard

We recommend that you assign a single Microsoft Entra user to Pingboard to test the provisioning configuration. Additional users can be assigned later.

## Configure user provisioning to Pingboard

This section guides you through connecting your Microsoft Entra ID to the Pingboard user account provisioning API. You also configure the provisioning service to create, update, and disable assigned user accounts in Pingboard that are based on user assignments in Microsoft Entra ID.

Tip

To enable SAML-based single sign-on for Pingboard, follow the instructions provided in the [Azure portal](https://portal.azure.com). Single sign-on can be configured independently of automatic provisioning, although these two features complement each other.

### To configure automatic user account provisioning to Pingboard in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.
3. If you already configured Pingboard for single sign-on, search for your instance of Pingboard by using the search field. Otherwise, select **Add** and search for **Pingboard** in the application gallery. Select **Pingboard** from the search results, and add it to your list of applications.
4. Select your instance of Pingboard, and then select the **Provisioning** tab.
5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Pingboard Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Pingboard. If the connection fails, ensure your Pingboard account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of the Provisioning properties page showing notification and deletion settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. In the **Attribute Mappings** section, review the user attributes to be synchronized from Microsoft Entra ID to Pingboard. The attributes selected as **Matching** properties are used to match the user accounts in Pingboard for update operations. Select **Save** to commit any changes. For more information, see [Customize user provisioning attribute mappings](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).
12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

For more information on how to read the Microsoft Entra provisioning logs, see [Report on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).

## Additional resources

- [Manage user account provisioning for enterprise apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Configure single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/pingboard-tutorial)
