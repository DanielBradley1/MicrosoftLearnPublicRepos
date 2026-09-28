<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/visitly-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-26 -->

# Configure Visitly for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps you perform in Visitly and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and deprovision users or groups to Visitly.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to software-as-a-service \(SaaS\) applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Visitly.
- Remove users in Visitly when they don't require access anymore.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/visitly-tutorial) to Visitly \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Visitly tenant](https://www.visitly.io/pricing/)
- A user account in Visitly with admin permissions

## Step 1: Assign users to Visitly

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users or groups that were assigned to an application in Microsoft Entra ID are synchronized.

Before you configure and enable automatic user provisioning, decide which users or groups in Microsoft Entra ID need access to Visitly. Then assign these users or groups to Visitly by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Visitly

- We recommend that you assign a single Microsoft Entra user to Visitly to test the automatic user provisioning configuration. More users or groups can be assigned later.
- When you assign a user to Visitly, you must select any valid application-specific role \(if available\) in the assignment dialog box. Users with the Default Access role are excluded from provisioning.

## Step 2: Set up Visitly for provisioning

Before you configure Visitly for automatic user provisioning with Microsoft Entra ID, you need to enable System for Cross-domain Identity Management \(SCIM\) provisioning on Visitly.

1. Sign in to [Visitly](https://app.visitly.io/login). Select **Integrations** > **Host Synchronization**.

   ![Screenshot of Host Synchronization.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/visitly-provisioning-tutorial/login.png)

2. Select the **Microsoft Entra ID** section.

   ![Screenshot of Microsoft Entra ID section.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/visitly-provisioning-tutorial/integration.png)

3. Copy the **API Key**. These values are entered in the **Secret Token** box on the **Provisioning** tab of your Visitly application.

   ![Screenshot of API Key.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/visitly-provisioning-tutorial/token.png)

## Step 3: Add Visitly from the gallery

To configure Visitly for automatic user provisioning with Microsoft Entra ID, add Visitly from the Microsoft Entra application gallery to your list of managed SaaS applications.

To add Visitly from the Microsoft Entra application gallery, follow these steps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.Visitly\*\*, select **Visitly** in the results panel, and then select **Add** to add the application.

   ![Screenshot of Visitly in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Step 4: Configure automatic user provisioning to Visitly

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users or groups in Visitly based on user or group assignments in Microsoft Entra ID.

Tip

To enable SAML-based single sign-on for Visitly, follow the instructions in the [Visitly single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/visitly-tutorial). Single sign-on can be configured independently of automatic user provisioning, although these two features complement each other.

### Configure automatic user provisioning for Visitly in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Visitly**.

   ![Screenshot of Visitly link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

3. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

4. Select **+ New configuration**.

   ![Screenshot of New configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

5. Under the Admin Credentials section, input the `https://api.visitly.io/v1/usersync/SCIM` and **API Key** values retrieved earlier in **Tenant URL** and **Secret Token**, respectively. Select **Test Connection** to ensure that Microsoft Entra ID can connect to Visitly. If the connection fails, make sure that your Visitly account has admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

6. Select **Create** to create your configuration.
7. Select **Properties** on the **Overview** page.
8. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

9. Select **Attribute Mapping** in the left panel and select **users**.
10. Review the user attributes that are synchronized from Microsoft Entra ID to Visitly in the **Attribute Mappings** section. The attributes selected as **Matching** properties are used to match the user accounts in Visitly for update operations. Select **Save** to commit any changes.

    ![Visitly user attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/visitly-provisioning-tutorial/userattribute.png)

11. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
12. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
13. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 5: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Connector limitations

Visitly doesn't support hard deletes. Everything is soft delete only.

## More resources

- [Manage user account provisioning for enterprise apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
