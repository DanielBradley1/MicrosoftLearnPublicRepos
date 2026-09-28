<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/leapsome-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Configure Leapsome for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Leapsome and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Leapsome.

Note

This article describes a connector built on top of the Microsoft Entra user Provisioning Service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

This connector is currently in Preview. For more information about previews, see [Universal License Terms For Online Services](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- \- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..
- A [Leapsome](https://www.Leapsome.com/pricing) tenant.
- A user account in Leapsome with Admin permissions.

## Assigning users to Leapsome

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Leapsome. Once decided, you can assign these users and/or groups to Leapsome by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to Leapsome

- It's recommended that a single Microsoft Entra user is assigned to Leapsome to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Leapsome, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Set up Leapsome for provisioning

1. Sign in to your [Leapsome Admin Console](https://www.Leapsome.com/app/#/login). Navigate to **Settings > Admin Settings**.

   ![Screenshot of Leapsome Admin Console.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/leapsome-provisioning-tutorial/leapsome-admin-console.png)

2. Navigate to **Integrations > SCIM User provisioning**.

   ![Screenshot of Leapsome Add SCIM.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/leapsome-provisioning-tutorial/leapsome-add-scim.png)

3. Copy the **SCIM Authentication Token**. This value is entered in the Secret Token field in the Provisioning tab of your Leapsome application.

   ![Screenshot of Leapsome Create Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/leapsome-provisioning-tutorial/leapsome-create-token.png)

## Add Leapsome from the gallery

Before configuring Leapsome for automatic user provisioning with Microsoft Entra ID, you need to add Leapsome from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Leapsome from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Leapsome**, select **Leapsome** in the search box.
4. Select **Leapsome** from results panel and then add the app. Wait a few seconds while the app is added to your tenant. ![Screenshot of Leapsome in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configuring automatic user provisioning to Leapsome

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Leapsome based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Leapsome, following the instructions provided in the [Leapsome Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/leapsome-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other

### To configure automatic user provisioning for Leapsome in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Leapsome**.

   ![Screenshot of the Leapsome link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Leapsome Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Leapsome. If the connection fails, ensure your Leapsome account has the required admin permissions and try again.

   Note

   Enter `https://www.leapsome.com/api/scim` in **Tenant URL**.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Leapsome in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Leapsome for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Leapsome API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

    ![Screenshot of Leapsome User Attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/leapsome-provisioning-tutorial/leapsome-user-attributes.png)

12. Review the group attributes that are synchronized from Microsoft Entra ID to Leapsome in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Leapsome for update operations. Select the **Save** button to commit any changes.

    ![Screenshot of Leapsome Group Attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/leapsome-provisioning-tutorial/leapsome-group-attributes.png)

13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Connector Limitations

- Leapsome requires **userName** to be unique.
- Leapsome only allows work email addresses to be saved.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
