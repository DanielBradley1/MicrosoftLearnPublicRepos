<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/dialpad-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# Configure Dialpad for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Dialpad and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Dialpad.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

> This connector is currently in Preview. For more information about previews, see [Universal License Terms For Online Services](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all).

## Capabilities supported

- Create users in Dialpad.
- Remove users in Dialpad when they don't require access anymore.
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..

- [A Dialpad tenant](https://www.dialpad.com/pricing/).
- A user account in Dialpad with Admin permissions.

## Assign Users to Dialpad

Microsoft Entra ID uses a concept called assignments to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Dialpad. Once decided, you can assign these users and/or groups to Dialpad by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to Dialpad

- It's recommended that a single Microsoft Entra user is assigned to Dialpad to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Dialpad, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the Default Access role are excluded from provisioning.

## Setup Dialpad for provisioning

Before configuring Dialpad for automatic user provisioning with Microsoft Entra ID, you need to retrieve some provisioning information from Dialpad.

1. Sign in to your [Dialpad Admin Console](https://dialpadbeta.com/login) and select **Admin settings**. Ensure that **My Company** is selected from the dropdown. Navigate to **Authentication > API Keys**.

   ![Screenshot of the Dialpad admin console, with the settings icon, My Company, Authentication, and A P I keys highlighted, and My Company selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dialpad-provisioning-tutorial/dialpad01.png)

2. Generate a new key by selecting **Add a key** and configuring the properties of your secret token.

   ![Screenshot of the A P I keys page in the Dialpad admin console. Add a key is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dialpad-provisioning-tutorial/dialpad02.png)


   ![Screenshot of the Edit A P I key page in the Dialpad admin console. The Save button is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dialpad-provisioning-tutorial/dialpad03.png)

3. Select the **Select to show value** button for your recently created API key and copy the value shown. This value is entered in the **Secret Token** field in the Provisioning tab of your Dialpad application.

   ![Dialpad Create Token](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dialpad-provisioning-tutorial/dialpad04.png)

## Add Dialpad from the gallery

To configuring Dialpad for automatic user provisioning with Microsoft Entra ID, you need to add Dialpad from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Dialpad from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Dialpad**, select **Dialpad** in the results panel. ![Dialpad in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)
4. Navigate to the **URL** highlighted below in a separate browser.

   ![Screenshot of a page displaying information about the Dialpad app. Under U R L, an address is listed and is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dialpad-provisioning-tutorial/dialpad05.png)

5. In the top right-hand corner, select **Log In > Use Dialpad online**.

   ![Screenshot of the Dialpad website. Log in is highlighted, and the Log in tab is open. Use Dialpad online is also highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dialpad-provisioning-tutorial/dialpad06.png)

6. As Dialpad is an OpenIDConnect app, choose to login to Dialpad using your Microsoft work account.

   ![Screenshot of the Start making calls page in the Dialpad website. The Log in with Office 365 button is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dialpad-provisioning-tutorial/loginpage.png)

7. After a successful authentication, accept the consent prompt for the consent page. The application will then be automatically added to your tenant and you be redirected to your Dialpad account.

## Configure automatic user provisioning to Dialpad

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Dialpad based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Dialpad in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Dialpad**.

   ![The Dialpad link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, input `https://dialpad.com/scim` in **Tenant URL**. Input the value that you retrieved and saved earlier from Dialpad in **Secret Token**. Select **Test Connection** to ensure Microsoft Entra ID can connect to Dialpad. If the connection fails, ensure your Dialpad account has Admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Dialpad in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Dialpad for update operations. Select the **Save** button to commit any changes.

    ![Dialpad User Attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/dialpad-provisioning-tutorial/dialpad07.png)

12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Connector limitations

- Dialpad doesn't support group renames today. This means that any changes to the **displayName** of a group in Microsoft Entra ID isn't updated and reflected in Dialpad.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
