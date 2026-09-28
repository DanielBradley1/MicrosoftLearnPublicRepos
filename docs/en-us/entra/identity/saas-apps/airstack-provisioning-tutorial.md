<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/airstack-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# Configure Airstack for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Airstack and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Airstack.

Note

This article describes a connector built on top of the Microsoft Entra user Provisioning Service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

Note

Airstack supports Long lived bearer token authentication.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- An Airstack tenant.
- A user account in Airstack with Admin permissions.

## Assigning users to Airstack

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Airstack. Once decided, you can assign these users and/or groups to Airstack by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to Airstack

- It's recommended that a single Microsoft Entra user is assigned to Airstack to test the automatic user provisioning configuration. Additional users and/or groups can be assigned later.
- When assigning a user to Airstack, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Setup Airstack for provisioning

1. Sign in to your Airstack Admin Console. Navigate to **Settings**.

   ![Airstack Admin Console](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/airstack-provisioning-tutorial/airstackadminmenu.png)

2. Navigate to **Azure Config** on the menu located to the left side of the screen.

   ![Airstack Add SCIM](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/airstack-provisioning-tutorial/azureconfig.png)

3. Select **Generate** button. Copy the **Secret Token for Azure**. This value is entered in the Secret Token field in the Provisioning tab of your Airstack application.

   ![Airstack Create Token](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/airstack-provisioning-tutorial/generatetoken.png)

## Add Airstack from the gallery

Before configuring Airstack for automatic user provisioning with Microsoft Entra ID, you need to add Airstack from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Airstack from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Airstack**, select **Airstack** in the search box.
4. Select **Airstack** from results panel and then add the app. Wait a few seconds while the app is added to your tenant. ![Airstack in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configuring automatic user provisioning to Airstack

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Airstack based on user and/or group assignments in Microsoft Entra ID.

Tip

You can also choose to enable SAML-based single sign-on for Airstack, following the instructions provided in the [Airstack Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/airstack-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other

### To configure automatic user provisioning for Airstack in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Airstack**.

   ![The Airstack link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Airstack Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Airstack. If the connection fails, ensure your Airstack account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Airstack in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Airstack for update operations. Select the **Save** button to commit any changes.

    ![Airstack User Attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/airstack-provisioning-tutorial/attributes.png)

12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
