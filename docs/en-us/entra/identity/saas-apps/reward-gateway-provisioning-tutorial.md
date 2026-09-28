<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/reward-gateway-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Configure Reward Gateway for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Reward Gateway and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Reward Gateway.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

This connector is currently in public preview. For more information about previews, see [Universal License Terms For Online Services](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..

- A [Reward Gateway tenant](https://www.rewardgateway.com/).
- A user account in Reward Gateway with Admin permissions.

## Assigning users to Reward Gateway

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Reward Gateway. Once decided, you can assign these users and/or groups to Reward Gateway by following the instructions in [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal).

## Important tips for assigning users to Reward Gateway

- It's recommended that a single Microsoft Entra user is assigned to Reward Gateway to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Reward Gateway, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Setup Reward Gateway for provisioning

Before configuring Reward Gateway for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on Reward Gateway.

1. Sign in to your [Reward Gateway Admin Console](https://rewardgateway.photoshelter.com/login/). Select **Integrations**.

   ![Screenshot of the Reward Gateway Admin Console with the Integrations option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/reward-gateway-provisioning-tutorial/image00.png)

2. Select **My Integration**.

   ![Screenshot of the two Integrations options with the My Integrations option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/reward-gateway-provisioning-tutorial/image001.png)

3. Copy the values of **SCIM URL \(v2\)** and **OAuth Bearer Token**. These values are entered in the Tenant URL and Secret Token field in the Provisioning tab of your Reward Gateway application.

   ![Screenshot of the My Integrations panel with the OAuth Bearer Token text box called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/reward-gateway-provisioning-tutorial/image03.png)

## Add Reward Gateway from the gallery

To configure Reward Gateway for automatic user provisioning with Microsoft Entra ID, you need to add Reward Gateway from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Reward Gateway from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Reward Gateway**, select **Reward Gateway** in the search box.
4. Select **Reward Gateway** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

   ![Screenshot of the Reward Gateway in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configuring automatic user provisioning to Reward Gateway

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Reward Gateway based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Reward Gateway, following the instructions provided in the [Reward Gateway Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/reward-gateway-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other.

### To configure automatic user provisioning for Reward Gateway in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of the Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Reward Gateway**.

   ![Screenshot of the Reward Gateway link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Reward Gateway Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Reward Gateway. If the connection fails, ensure your Reward Gateway account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of the Provisioning properties page showing notification and deletion settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select users.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Reward Gateway in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Reward Gateway for update operations. Select the **Save** button to commit any changes.

    ![Screenshot of the Attribute Mappings section with six mappings displayed.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/reward-gateway-provisioning-tutorial/user-attributes.png)

12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts) article.
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

For more information on how to read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).

## Connector limitations

Reward Gateway doesn't support group provisioning currently.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

[Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
